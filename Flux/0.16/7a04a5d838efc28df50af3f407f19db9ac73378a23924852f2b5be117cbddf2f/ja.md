```
@layer [showtype] MyModel [trainable=(field1,...)]
```

このマクロは、カスタム型に便利な機能を追加し、ニューラルネットワークのレイヤー、モジュール、または全体のモデルとして機能します。

オプションのキーワード `trainable` を使用すると、モデルのどのフィールドをトレーニング可能にするかを指定できます。すべての `fieldnames(MyModel)` をトレーニング可能と仮定するのではなく、特定のフィールドを指定できます。Fluxに対して、関数やサイズのような非配列オブジェクトを無視するように指示する必要はありません。これは、あなたの型のために [`trainable(::MyModel)`](@ref Optimisers.trainable) を定義することでも行えます。

このマクロは、きれいに印刷するための3引数 `show(::IO, ::MIME"text/plain", ::MyModel)` のオーバーロードも処理します。オプションの引数 `showtype` は、以下のいずれかの値を取ることができます：

  * `:expand` (デフォルト)：これは、`Chain` のようなコンテナ型の表現を拡張しますが、配列のみを含む `Dense` のような型の互換性のある表現を維持します。
  * `:noexpand`：これは、あなたの型が他のレイヤーを含む場合に使用しますが、表現をシンプルに保ちたい場合に使用します。
  * `:ignore`：きれいに印刷することをオプトアウトします。

おそらく、2引数 `show(::IO, ::MyModel)` を定義したいでしょうが、マクロはこれには触れません。

異なるオプションでマクロを再実行してもすべてのメソッドが削除されない場合があるため、再起動が必要です。

# 例

```jldoctest
julia> struct Trio; a; b; c end

julia> tri = Trio(Dense([1.1 2.2], [0.0], tanh), Dense(hcat(3.3), false), Dropout(0.4))
Trio(Dense(2 => 1, tanh), Dense(1 => 1; bias=false), Dropout(0.4))

julia> Flux.@layer Trio

julia> tri  # これでレイヤーはChainのように印刷されます
Trio(
  Dense(2 => 1, tanh),                  # 3 パラメータ
  Dense(1 => 1; bias=false),            # 1 パラメータ
  Dropout(0.4),
)                   # 合計: 3 配列, 4 パラメータ, 240 バイト。

julia> Flux.@layer :noexpand Trio trainable=(a,b)

julia> tri  # これでレイヤーはコンパクトに印刷されます
Trio(Dense(2 => 1, tanh), Dense(1 => 1; bias=false), Dropout(0.4))  # 4 パラメータ

julia> opt_state = Flux.setup(Adam(), tri); # `c` はオプティマイザの状態に含まれません
```

このマクロは、FluxをEnzymeと一緒に使いやすくするためのメソッドも追加します。

  * `Duplicated(m::Layer)` は、勾配のコピーを割り当てます（初期値はゼロ）。
  * これは呼び出し可能で、`(m::Duplicated{<:Layer})(x...) = m.val(x...)`
  * `show(io, mime, ::Duplicated{<:Layer})` のためのきれいな印刷

```
