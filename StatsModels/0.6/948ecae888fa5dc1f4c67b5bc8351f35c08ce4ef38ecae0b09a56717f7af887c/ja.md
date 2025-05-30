```
HypothesisCoding(hypotheses::AbstractMatrix; levels=nothing, labels=nothing)
```

カテゴリ変数を*仮説行列*の観点からコーディングする方法を指定します。$k$レベルの変数について、これは$k-1 \times k$の行列である必要があります。行列の各行は、予測因子の$k$レベルの下での平均結果に関する仮説に対応します。行のエントリは、これらの$k$の平均に割り当てられた重みを示し、回帰モデルの対応する予測因子はこれらのセル平均の重み付き合計を推定します。

例えば、A、B、C、Dの4つのレベルを持つ変数があり、レベルAとBの平均結果の差がゼロと異なるという仮説をテストしたい場合、対応する仮説行列の行は`[-1, 1, 0, 0]`になります。同様に、BとCの差がゼロと異なるかどうかをテストするための仮説ベクトルは`[0, -1, 1, 0]`になります。各「連続差」仮説をテストするために、完全な仮説行列は次のようになります。

```jldoctest hyp
julia> sdiff_hypothesis = [-1  1  0  0
                            0 -1  1  0
                            0  0 -1  1];
```

コントラストは、擬似逆行列を取ることによって仮説行列から導出されます。

```jldoctest hyp
julia> using LinearAlgebra

julia> sdiff_contrasts = pinv(sdiff_hypothesis)
4×3 Array{Float64,2}:
 -0.75  -0.5  -0.25
  0.25  -0.5  -0.25
  0.25   0.5  -0.25
  0.25   0.5   0.75
```

上記の行列は、`HypothesisCoding`インスタンスから[`ContrastsMatrix`](@ref)を構築することによって生成されるものです。

```jldoctest hyp
julia> StatsModels.ContrastsMatrix(HypothesisCoding(sdiff_hypothesis), ["a", "b", "c", "d"]).matrix
4×3 Array{Float64,2}:
 -0.75  -0.5  -0.25
  0.25  -0.5  -0.25
  0.25   0.5  -0.25
  0.25   0.5   0.75
```

このような「連続差」コントラストの解釈は、仮説行列として表現されると明確ですが、コントラスト行列を見ただけでは明らかではありません。この理由から、`HypothesisCoding`は`ContrastsCoding`よりもカスタムコントラストコーディングスキームを指定するために好まれます。

オプションの引数`levels`と`labels`は、仮説行列の列（データのレベルに対応）と行（テストされた仮説に対応）の名前を（順番に）提供します。`labels`は、これらのコントラストによって生成されるモデル行列の列の名前も決定します。

# 参考文献

Schad, D. J., Vasishth, S., Hohenstein, S., & Kliegl, R. (2020). How to capitalize on a priori contrasts in linear (mixed) models: A tutorial. *Journal of Memory and Language, 110*, 104038. https://doi.org/10.1016/j.jml.2019.104038
