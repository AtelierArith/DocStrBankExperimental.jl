```
@addmethod func(args...;kwargs...) = body
@addmethod function func(args...;kwargs...) 
	body
end
```

This simple macro modifies a function definition expression (only when called from a Pluto notebook) to prepend the name of the module defining the function (here called `DefiningModule`) to the method definition.

So the code

```julia
@addmethod func(args...;kwargs...) = something
```

is simply translated to

```julia
DefiningModule.func(args...;kwargs...) = something
```

when called from a Pluto notebook, and to:

```julia
func(args...;kwargs...) = something
```

when called outside of Pluto.

This is useful to avoid multiple definition errors inside Pluto but has the caveat that defining a method with `@addmethod` does not trigger a reactive run of all cells that call the modified function. This also mean that when removing the cell with the `@addmethod` call, the actual method added to the `DefiningModule` will not be automatically erased by Pluto and will still accessible until it is not overwritten with another method with the same signature. 

This is easy to fix in the case of adding methods to modules loaded with `@frompackage`/`@fromparent` as reloading the module is sufficient to remove the hanging method.

See this video for an example:

![Link to Video](https://user-images.githubusercontent.com/12846528/236472989-da86a311-4501-4966-9f0b-1298bbd9d53b.mp4)

See also: [`@frompackage`](@ref), [`@fromparent`](@ref)
