```julia
struct TuningNUTS{M, D}
```

サンプリング中にステップサイズ `ϵ` を調整し、ブロックの最後で運動エネルギーのメトリックを調整します。後者の方法は型パラメータ `M` によって決定され、次のいずれかになります。

1. `Diagonal` は対角メトリック（デフォルト）、
2. `Symmetric` は密なメトリック、
3. `Nothing` は変更されないメトリック。

# 結果

次のフィールドを持つ `NamedTuple`：

  * `posterior_matrix`、位置ベクトルの行列、`[parameter_index, draw_index]` でインデックス付け
  * `tree_statistics`、各サンプルの木の統計のベクトル
  * `ϵs`、各サンプルのステップサイズのベクトル

# フィールド

  * `N`: サンプルの数。
  * `stepsize_adaptation`: 二重平均化パラメータ。
  * `λ`: 分散を正規化するための正則化係数。推定された共分散行列 `Σ` は、対角の中央値 $σ²$ に向かって `λ` によって再スケーリングされます。コンストラクタには合理的なデフォルトがあります。
