The Multibreak package provides the `@multibreak` macro for breaking out of, and optionally continuing, several nested loops at once.

The simplest use is of the form

```
using Multibreak

@multibreak for i = 1:5
    for j = 1:5
        break; break
    end
end
```

Read the tutorial at /home/terasaki/.julia/packages/Multibreak/vatgU/test/tutorial.jl or https://github.com/GunnarFarneback/Multibreak.jl/blob/master/test/tutorial.jl for the full documentation.
