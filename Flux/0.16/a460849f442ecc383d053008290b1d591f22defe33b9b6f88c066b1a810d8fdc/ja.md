```
Chain(layers...)
Chain(name = layer, ...)
```

複数のレイヤー/関数を収集し、与えられた入力に対して順番に呼び出すことができます。インデックス付けやスライスをサポートしており、`m[2]`や`m[1:end-1]`が使用でき、名前が付けられている場合は、`m[:name] == m[1]`などが可能です。

# 例

```jldoctest
julia> m = Chain(x -> x^2, x -> x+1);

julia> m(5) == 26
true

julia> m = Chain(Dense(10 => 5, tanh), Dense(5 => 2));

julia> x = rand32(10, 32);

julia> m(x) == m[2](m[1](x))
true

julia> m2 = Chain(enc = Chain(Flux.flatten, Dense(10 => 5, tanh)), 
                  dec = Dense(5 => 2));

julia> m2(x) == (m2[:dec] ∘ m2[:enc])(x)
true
```

チェーンは複数の引数で呼び出すことができ、これはこれらの引数の1つのタプルで呼び出すことと同等です。このようなタプルは[`Parallel`](@ref)によって複数の引数と同じ意味として理解されます：

```jldoctest
julia> Chain(println, println)(1, 2, 3)  # 3つの引数がタプルになる
(1, 2, 3)
nothing

julia> Chain(x->@show(x), Parallel(+, inv, abs2))(4, 5)  # 1/4 + 5^2を返す
x = (4, 5)
25.25
```

大規模なモデルの場合、コンパイル時間を短縮できる特別な型不安定なパスがあります。これは、レイヤーのベクトルを供給することで使用できます `Chain([layer1, layer2, ...])`。この機能はやや実験的であるため、注意が必要です！
