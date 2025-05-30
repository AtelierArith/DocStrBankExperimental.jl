```
@allow_boxed_captures expr
```

By default, OhMyThreads.jl will detect and error on multithreaded code which references local variables which are 'boxed' – something that happens if the variable could be re-bound in multiple scopes. This process can cause very sublte bugs in multithreaded code by creating silent race conditions, e.g.

```julia
let
    function wrong()
        tmap(1:10) do i
            A = i # define A for the first time (lexically)
            sleep(rand()/10)
            A # user is trying to reference local A only
        end
    end
    @show wrong()
    A = 1 # boxed! this hoists "A" to the same variable as in `wrong` but presumably the user wanted a new one
end
```

In this example, you might expect to get `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`, but you would actually observe incorrect results because `A` is 'boxed'. The fix for this would be to write something like

```julia
let
    function right()
        tmap(1:10) do i
            local A = i
            sleep(rand()/10)
            A 
        end
    end
    @show right()
    A = 1
end
```

However, if you are really sure you want to bypass OhMyThreads's error mechanism, you can use `@allow_boxed_captures` to wrap code you believe is okay, e.g.

```julia-repl
julia> let A = 1 
           @allow_boxed_captures tmap(1:10) do i
               A = i
               sleep(rand()/10)
               A # race condition!
           end
       end
10-element Vector{Int64}:
 4
 2
 7
 2
 2
 8
 6
 8
 7
 2
```

This is a dynamically scoped construct, so this effect will apply to *all* nested code inside of `expr`.

See also `@disallow_boxed_captures`
