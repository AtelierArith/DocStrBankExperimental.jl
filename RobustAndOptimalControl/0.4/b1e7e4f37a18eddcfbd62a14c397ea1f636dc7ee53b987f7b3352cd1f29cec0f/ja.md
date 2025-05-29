```
fig = mvnyquistplot(sys, w;  unit_circle=true, hz = false, kwargs...)
```

`LTISystem`のナイキストプロットを作成します。周波数ベクトル`w`を提供する必要があります。

  * `unit_circle`: 単位円を表示するかどうか

`hz=true`の場合、ホバー情報はヘルツで表示されますが、入力周波数ベクトルは依然としてrad/sとして扱われます。

`kwargs`はプロットへの引数として送信されます。

# 例

```julia
w = 2π .* exp10.(LinRange(-2, 2, 500))
W = makeweight(0.40, 15, 3) # 不確実なダイナミクスのための周波数重み
Pn = tf(1, [1/60, 1]) |> ss # 名目プラント
d = δss(1,1)                # 不確実なダイナミクス

Pd = Pn*(I(1) + W*d)        # Pnの入力に対する重み付けされた動的不確実性
Pp = rand(Pd, 200)          # 不確実なプラントをサンプリング
Gcl = lft(Pd, ss(-1))       # 閉ループシステム
structured_singular_value(Gcl) # 1より大きい => ロバストに安定していない
unsafe_comparisons(true)
mvnyquistplot(Pp, w, points=true) # MVナイキストプロットがいくつかのサンプルで原点を囲む => ロバストに安定していない
```
