```
@import LongModuleName as alias
@import LongModuleName.object as alias
```

Load the module `LongModuleName` with `import` and binds it to `alias`. Can also be used for specific objects inside the module. The resulting expression is roughly equivalent to

```julia
baremodule $(gensym())
    import LongModuleName.object
end
const alias = $(gensym()).LongModuleName
```
