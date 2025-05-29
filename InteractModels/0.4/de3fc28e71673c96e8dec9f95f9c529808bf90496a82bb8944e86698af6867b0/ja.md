```
InteractModel(f, model)
```

独自の Interact.jl インターフェースを生成する [`AbstractModel`](@ref) です。各モデルの [`Param`](@ref) に対してスライダーが生成され、モデルを更新します。スライダーが更新されると、ユーザー定義の関数 `f` に更新されたモデルが渡され、新しい出力が生成されます - WebIO.jl ノードに表示されるもの、例えば Plots.jl プロットのように。

スライダーが変更されると、親モデルが更新されるため、`parent(model)` は最新の状態を返します。

## 引数

  * `f`: モデルオブジェクトを引数として受け取る関数ですが、`Param` フィールドはその値に置き換えられます。通常は `do` ブロックです。
  * `model`: 一部のフィールドに [`Param`](@ref) オブジェクトを持つ任意のオブジェクト。

## Param フィールド

モデル内の `Param` オブジェクトは、スライダー範囲を定義するために `range` または `bounds` フィールドを含む必要があります - それぞれ `AbsractRange` または `NTuple{2}` を保持します。

オプションで、`Param` には以下も含めることができます：

  * フィールド名の代わりに使用する `label` フィールド
  * マウスホバー時のテキストに使用する `desciption` フィールド

## キーワード引数

  * `title`: `""` ウィンドウタイトルを設定します。必要な場合。
  * `submodel`: `Nothing`。スライダーをラベル付きのサブセクションにグループ化する `Type` または `Union`。
  * `throttle`: `0.1`。スライダーのスロットル、秒単位。パフォーマンスを向上させるために調整します。
  * `layout`: `vbox`。これは、タイトル、出力、およびスライダー（すべて WebIO ノード）を組み合わせて1つの WebIO ノードにする任意の3引数関数です。このメソッドを使用して、必要な追加のレイアウトを行うことができます。

## 例

これは、Interact.jl の例から適応された `NamedTuple` モデルの簡単な例です。これは、アトムのプロットペインに表示されます：

```julia
using InteractModels, Interact, ColorSchemes, Colors

color(i) = Colors.hex(colors[i%length(colors)+1])
colors = ColorSchemes.viridis
width, height = 700, 300
nsamples = 256

model = (;
    sample_step=Param(val=0.05, range=0.01:0.001:0.1, label="サンプルステップ"),
    phase=Param(val=0.0, range=0:0.1:2pi, label="位相"),
    radii=Param(val=20,range=0:0.1:60, label="半径")
)

ui = InteractModel(model; submodel=Nothing, throttle=0.1) do m
    cxs_unscaled = [i * m.sample_step + m.phase for i in 1:nsamples]
    cys = sin.(cxs_unscaled) .* height/3 .+ height/2
    cxs = cxs_unscaled .* width/4pi
    c = (dom"svg:circle[cx=$(cxs[i]), cy=$(cys[i]), r=$(m.radii), fill=#$(color(i))]"()
         for i in 1:nsamples)
    return dom"svg:svg[width=$width, height=$height]"(c...)
end
```
