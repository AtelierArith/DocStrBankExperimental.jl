```
@compact(kw...) do x
    ...
    @return y # optional (but recommended for best performance)
end
@compact(kw...) do x, p
    ...
    @return y # optional (but recommended for best performance)
end
@compact(forward::Function; name=nothing, dispatch=nothing, parameters...)
```

`parameters`をキーワードの形で指定し、（通常は`do`ブロックとして）フォワードパスのための関数を指定することでレイヤーを作成します。`@compact`は、Luxでトレーニング可能なローカル変数を作成する特化型の`let`ブロックのように考えることができます。宣言された変数名は、`forward`関数の本体内で使用できます。通常のLuxモデルとは異なり、フォワード関数は状態を明示的に管理する必要はありません。

`p`を使ったバージョンを定義することで、フォワードパスでパラメータにアクセスできます。これは、パラメータを明示的に渡す必要があるSciMLツールと一緒に使用する際に便利です。

## 予約済みKwargs:

1. `name`: レイヤーの名前。
2. `dispatch`: 構築されたレイヤーは`Lux.CompactLuxLayer{dispatch}`型を持ち、カスタムディスパッチに使用できます。

!!! tip
    `@compact`の使用例についてはLuxのチュートリアルを確認してください。


kwargsをスプラットして渡す場合、それらはそのまま関数本体に渡されます。これは、スプラットされたkwargsにLuxレイヤーが含まれている場合、それがCompactLuxLayerに登録されないことを意味します。さらに、すべてのデバイス関数はこれらのkwargsをリーフとして扱います。

## 特殊構文

  * `@return`: このマクロは実際には存在しませんが、`@compact`ブロックから値を返すために使用されます。このマクロが存在しない場合、クロージャに依存する必要があり、逆伝播でパフォーマンスのペナルティが発生する可能性があります。

      * 最後の`@return`マクロの後に文があると、正しくないコードになる可能性があります。
      * `@return return x`のようなことはしないでください。これは、`<new var> = return x`のような意味のないコードを生成します。基本的に、`@return <expr>`は、変数に代入できる任意の式をサポートします。
      * このマクロは「存在しない」ため、`using Lux: @return`としてインポートすることはできません。単にコード内で使用すれば、`@compact`はそれを理解します。
  * `@init_fn`: レイヤーのパラメータまたは状態を初期化するために使用される関数を提供します。詳細については[`@init_fn`](@ref)のドキュメントを参照してください。
  * `@non_trainable`: 値を非トレーニング可能としてマークします。これにより、通常のチェックをバイパスし、値をレイヤーの状態に配置します。詳細については[`@non_trainable`](@ref)のドキュメントを参照してください。

# 拡張ヘルプ

## 例

ここに線形モデルがあります：

```jldoctest
julia> using Lux, Random

julia> r = @compact(w=ones(3)) do x
           @return w .* x
       end
@compact(
    w = 3-element Vector{Float64},
) do x
    return w .* x
end       # 合計: 3 パラメータ,
          #        プラス 0 状態。

julia> ps, st = Lux.setup(Xoshiro(0), r);

julia> r([1, 2, 3], ps, st)  # xは[1, 1, 1]に設定されます。
([1.0, 2.0, 3.0], NamedTuple())
```

バイアスと活性化を持つ線形モデルがあります：

```jldoctest
julia> d_in = 5
5

julia> d_out = 3
3

julia> d = @compact(W=ones(d_out, d_in), b=zeros(d_out), act=relu) do x
           y = W * x
           @return act.(y .+ b)
       end
@compact(
    W = 3×5 Matrix{Float64},
    b = 3-element Vector{Float64},
    act = relu,
) do x
    y = W * x
    return act.(y .+ b)
end       # 合計: 18 パラメータ,
          #        プラス 1 状態。

julia> ps, st = Lux.setup(Xoshiro(0), d);

julia> d(ones(5, 2), ps, st)[1] # 出力として3×2行列。
3×2 Matrix{Float64}:
 5.0  5.0
 5.0  5.0
 5.0  5.0

julia> ps_dense = (; weight=ps.W, bias=ps.b);

julia> first(d([1, 2, 3, 4, 5], ps, st)) ≈
       first(Dense(d_in => d_out, relu)([1, 2, 3, 4, 5], ps_dense, NamedTuple())) # 密なレイヤーに相当
true
```

最後に、シンプルなMLPがあります。このモデルは、他のLuxモデルと同様にトレーニングできます：

```jldoctest
julia> n_in = 1;

julia> n_out = 1;

julia> nlayers = 3;

julia> model = @compact(w1=Dense(n_in, 128),
           w2=[Dense(128, 128) for i in 1:nlayers], w3=Dense(128, n_out), act=relu) do x
           embed = act.(w1(x))
           for w in w2
               embed = act.(w(embed))
           end
           out = w3(embed)
           @return out
       end
@compact(
    w1 = Dense(1 => 128),               # 256 パラメータ
    w2 = NamedTuple(
        1 = Dense(128 => 128),          # 16_512 パラメータ
        2 = Dense(128 => 128),          # 16_512 パラメータ
        3 = Dense(128 => 128),          # 16_512 パラメータ
    ),
    w3 = Dense(128 => 1),               # 129 パラメータ
    act = relu,
) do x
    embed = act.(w1(x))
    for w = w2
        embed = act.(w(embed))
    end
    out = w3(embed)
    return out
end       # 合計: 49_921 パラメータ,
          #        プラス 1 状態。

julia> ps, st = Lux.setup(Xoshiro(0), model);

julia> size(first(model(randn(n_in, 32), ps, st)))  # 出力として1×32行列。
(1, 32)

julia> using Optimisers, Zygote

julia> x_data = collect(-2.0f0:0.1f0:2.0f0)';

julia> y_data = 2 .* x_data .- x_data .^ 3;

julia> optim = Optimisers.setup(Adam(), ps);

julia> loss_initial = sum(abs2, first(model(x_data, ps, st)) .- y_data);

julia> for epoch in 1:1000
           loss, gs = Zygote.withgradient(
               ps -> sum(abs2, first(model(x_data, ps, st)) .- y_data), ps)
           Optimisers.update!(optim, ps, gs[1])
       end;

julia> loss_final = sum(abs2, first(model(x_data, ps, st)) .- y_data);

julia> loss_initial > loss_final
true
```

モデルに`name`を指定することもでき、これはデフォルトの出力の代わりに使用され、モデルを構築するために使用されたコードの逐語的な表現を提供します：

```jldoctest
julia> model = @compact(w=rand(3), name="Linear(3 => 1)") do x
           @return sum(w .* x)
       end
Linear(3 => 1)      # 3 パラメータ
```

これは、`@compact`を使用して複雑なモデルを階層的に構築し、`Chain`内で使用する際に便利です。

!!! tip "型の安定性"
    入力関数`f`が型安定であるが、生成されたモデルが型安定でない場合、それはバグとして扱われるべきです。そのようなケースを見つけた場合は、問題を報告していただけるとありがたいです。


!!! warning "パラメータ数"
    配列パラメータは、横にパラメータの数を表示しません。ただし、下部に表示されるパラメータの総数にはカウントされます。


```
