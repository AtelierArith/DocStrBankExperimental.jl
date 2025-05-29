```
@loop call
@loop n call
@loop bool_expr call
```

`call`を中断されるまで無限に繰り返すか、`n`回繰り返し、出力は破棄されます。最初の引数として式が与えられた場合、それは`Bool`を返さなければならず、`false`になるまで繰り返しが行われます。

```julia-repl
julia> @loop println("Hello, World!")
Hello, World!
Hello, World!^C
ERROR: InterruptException:
...

julia> @loop 2 println("Hello, World!")
Hello, World!
Hello, World!

julia> @loop rand() > 0.5 println("Hello, World!")
Hello, World!
```
