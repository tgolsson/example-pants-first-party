# Local `package main` with `main.go`
go_package(
    name="pkg",
    sources=["main.go"],
)

# OK: Local package `main` as an executable target
go_binary(
    name="bin",
    main=":pkg"
)

# OK: remote package main as an executable target, but slightly pointless
go_binary(
    name="third-party-bin",
    main="//:root#github.com/tgolsson/example-pants-third-party/cmd/hello"
)

# Not OK: If this actually got linked it'd be two mains. But the explicit dep here is just ignored. Actually using it is a compilation error.
go_package(
    name="pkg2",
    sources=["main.go"],
    dependencies=["//:root#github.com/tgolsson/example-pants-third-party/cmd/hello"], # this dependency isn't used and can't be used but pants doesn't scream at me.
)

# No idea what _dependencies does here; but it's also ignored.
go_binary(
    name="bin2",
    main=":pkg2",
    _dependencies=["//:root#github.com/tgolsson/example-pants-third-party/cmd/hello"]
)
