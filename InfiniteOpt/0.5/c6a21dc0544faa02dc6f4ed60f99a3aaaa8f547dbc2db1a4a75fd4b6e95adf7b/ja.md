```
num_derivatives(model::InfiniteModel)::Int
```

`model`で定義された導関数の数を返します。ネストされた導関数は、その構成要素に従ってカウントされることに注意してください（例： $\frac{d^2 x(t)}{dt^2} =$\frac{d}{dt}\left(\frac{d x(t)}{dt} \right)`` は2つの導関数としてカウントされます。）

**例**

```julia-repl
julia> num_derivatives(model)
12
```
