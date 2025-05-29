LPVスペクトル推定結果タイプ。

追加のヘルプについては `ls_spectral_lpv` を参照してください。

このタイプのオブジェクトは、`Plots.jl` がインストールされている場合にプロットできます。追加の属性を持つ通常のプロット構文を使用してください。

```
normalization= :none / :sum / :max
normdim = :freq / :v # normalization= :sum または :max の場合のみ適用
dims = 2 または 3 (デフォルト = 2)
```

フィールド：

```
Y::AbstractVector
X::AbstractVector
V::AbstractVector
w
Nv
λ
coulomb::Bool
normalize::Bool
x                   # 推定されたパラメータ
Σ                   # 推定されたパラメータの共分散
```
