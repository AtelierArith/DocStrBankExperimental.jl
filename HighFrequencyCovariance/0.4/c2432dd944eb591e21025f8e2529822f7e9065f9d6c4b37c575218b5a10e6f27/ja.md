```
bnhls_covariance(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts);
    regularisation::Union{Missing,Symbol} = :covariance_default,
    regularisation_params::Dict = Dict(),
    only_regulise_if_not_PSD::Bool = false,
    kernel::HFC_Kernel{<:Real} = parzen,
    H::Real = kernel.c_star * (mean(map(a -> length(ts.groupingrows[a]), assets)))^0.6,
    m::Integer = 2,
)
```

これはBNHLS(2011)の多変量実現カーネルを用いて共分散を計算します。

### 入力

  * `ts` - ティックデータ。
  * `assets` - ボラティリティを推定したい資産。
  * `regularisation` - 使用する正則化手法を表すシンボル。欠損の場合は正則化は行われません。
  * `regularisation_params` - 正則化アルゴリズムで使用されるキーワード引数。
  * `only_regulise_if_not_PSD` - 行列がすでにPSDでない場合にのみ正則化を試みるべきか。
  * `kernel` - 使用されるカーネル。詳細は論文を参照してください。
  * `H` - 推定に使用されるラグ/リードの数。詳細は論文を参照してください。
  * `m` - 平均化するエンドリターンの数。

### 戻り値

  * `CovarianceMatrix`。

### 参考文献

Barndorff-Nielsen, O., Hansen, P.R., Lunde, A., Shephard, N. 2011. - 論文全体ですが、特に2.2、2.3を参照してください。カーネルは表1にあります。Hの選択については論文の3.4節で議論されています。
