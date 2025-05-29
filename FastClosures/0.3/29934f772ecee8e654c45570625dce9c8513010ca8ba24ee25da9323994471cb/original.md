```
@closure closure_expression
```

Wrap the closure definition `closure_expression` in a let block to encourage the julia compiler to generate improved type information.  For example:

```julia
callfunc(f) = f()

function foo(n)
   for i=1:n
       if i >= n
           # Unlikely event - should be fast.  However, capture of `i` inside
           # the closure confuses the julia-0.6 compiler and causes it to box
           # the variable `i`, leading to a 100x performance hit if you remove
           # the `@closure`.
           callfunc(@closure ()->println("Hello $i"))
       end
   end
end
```

There's nothing nice about this - it's a heuristic workaround for some inefficiencies in the type information inferred by the julia 0.6 compiler. However, it can result in large speedups in many cases, without the need to restructure the code to avoid the closure.
