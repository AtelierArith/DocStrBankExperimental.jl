```julia
continuation(
    prob,
    algdc,
    contParams;
    verbosity,
    plot,
    linear_algo,
    dot_palc,
    callback_newton,
    filename,
    normC,
    kwcont...
)

```

この関数は、方程式 `F(x,p) = 0` に対する解の曲線の集合 `γ(s) = (x(s), p(s))` を、Farrell, Patrick E., Casper H. L. Beentjes, および Ásgeir Birkisson によって説明された **デフレート継続** のアルゴリズムに基づいて計算します。「Disconnected Bifurcation Diagrams の計算」。ArXiv:1603.00809 [Math], 2016年3月2日。 http://arxiv.org/abs/1603.00809。

`contParams` のオプションに応じて、各ブランチの分岐点を特定できます。異なる予測子を `alg` を使用して指定できることに注意してください。

# 引数:

  * `prob::AbstractBifurcationProblem` 分岐問題
  * `alg::DefCont` デフレート継続アルゴリズム、[`DefCont`](@ref) を参照
  * `contParams` 継続のためのパラメータ。オプションに関する詳細は [`ContinuationPar`](@ref) を参照

# オプション引数:

  * `plot = false` 計算中に解をプロットするかどうか、
  * `callback_newton` ニュートン反復のためのコールバック。`newton` のドキュメントを参照。前処理器を変更したり、ニュートン反復に影響を与えるために使用できます。アルゴリズムのデフレート部分では、新しいブランチを探す際に、コールバックにキーワード引数 `fromDeflatedNewton = true` が渡され、ユーザーに継続部分（通常のニュートン）ではないことを伝えます。
  * `verbosity::Int` 継続プロセス中に印刷される情報の量を制御します。`{0,⋯,5}` に属する必要があります。
  * `normC = norm` ニュートン解法で使用されるノルム、
  * `dot_palc = (x, y) -> dot(x, y) / length(x)` 重み付き内積を定義するために使用される内積（それぞれノルム） $\|(x, p)\|^2_\theta$ 制約 $N(x, p)$ において（オンラインドキュメントの [PALC](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/PALC/) を参照）。この引数は、状態空間の次元が変化する問題（メッシュ適応など）において、例えば `1/length(x)` の因子を削除するために使用できます。

# 出力:

  * `contres::DCResult` 計算されたブランチを含む複合型。詳細については [`ContResult`](@ref) を参照してください。
