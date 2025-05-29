```julia
get_normal_form(
    prob,
    br,
    id_bif;
    nev,
    verbose,
    ζs,
    lens,
    Teigvec,
    scaleζ,
    autodiff,
    δ,
    k...
)

```

周期軌道の正準形 (NF) を計算します。周期軌道に特有の追加のキーワード引数について詳述します。

# オプション引数

  * `prm = true` ポアンカレ帰納写像 (PRM) を使用して正準形を計算します。false の場合は、イオスの正準形を使用します。
  * `nev = length(eigenvalsfrombif(br, id_bif))`,
  * `verbose = false`,
  * `ζs = nothing` 固有ベクトルを渡します
  * `lens = getlens(br)`,
  * `Teigvec = _getvectortype(br)` 固有ベクトルのタイプ (GPU に便利な場合があります)
  * `scaleζ = norm` 固有ベクトルをスケールします
  * `prm = true` ポアンカレ帰納写像に基づく NF (`prm=true`) またはイオスの方法。
  * `autodiff = false` 正準形計算の一部で自動微分または有限差分を使用します
  * `detailed = true` 詳細な正準形を取得するため
  * `δ = getdelta(prob)` 有限差分に使用されるデルタ

# 注意事項

コレクションの場合、周期倍増およびネイマーク-サッカー分岐の NF を計算するためのデフォルトの方法はイオスの方法です。
