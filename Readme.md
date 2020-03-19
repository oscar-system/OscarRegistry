# OscarRegistry

At the moment mostly for testing the migration to [Pkg Artifacts](https://julialang.org/blog/2019/11/artifacts/) (via JLL packages) for all binary dependencies.

Can also be used to test and share versioned packages that are not yet registered in the official Julia registry.

In the end all binary artifacts should be available from the main Julia
registry, for this one needs to create a pull request to [Yggdrasil](https://github.com/JuliaPackaging/Yggdrasil).

*Note:* Pkg artifacts need Julia version 1.3 or newer.

## Usage

Add the registry via:

```julia
pkg> registry add https://github.com/oscar-system/OscarRegistry
```

Now packages from this registry can be added as usual via `Pkg.add` and `using`.

The registry will be cloned in `$HOME/.julia/registries/OscarRegistry`.

## Development usage

To add packages to the custom registry one has to use LocalRegistry package via:
```julia
pkg> add https://github.com/GunnarFarneback/LocalRegistry.jl
julia> using LocalRegistry
```

After a package has been `dev`d it can be added or updated in the registry with:
```julia
julia> register("polymake_jll","OscarRegistry")
```

It will create a commit in the registry but not push automatically so you need to go to `$HOME/.julia/registries/OscarRegistry` and push manually.
You might need to change the remote url first:
```
$ git remote set-url origin git@github.com:oscar-system/OscarRegistry
```

