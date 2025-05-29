```
aaa(Z, F; tol=1e-13, mmax=150, verbose=false, clean=true, do_sort=false) -> r::AAAapprox
```

データ `F` の `Z` 上の有理近似を AAA アルゴリズムを使用して計算します。

# 引数

  * `Z`: サンプルポイントのベクトル。
  * `F`: `Z` のポイントでの値のベクトル。
  * `tol`: 相対許容誤差。
  * `mmax`: 分子と分母の次数は最大で `(mmax-1, mmax-1)` です。
  * `verbose`: `true` の場合、計算中に詳細情報を出力します。
  * `clean`: `true` の場合、Froissart ダブレットを検出して削除します。
  * `do_sort`: `true` の場合、`Z` の値（およびそれに対応する `F`）を昇順にソートします。

# 戻り値

  * `r::AAAapprox`: 関数として呼び出される近似体を表す構造体。構造体には、`z, f, w` = サポートポイント、関数値、重みのベクトルと、`errvec` = 各ステップでの誤差のベクトルがあります。

注 1. MATLAB バージョンからの変更点には、関数シグネチャでの `Z` と `F` の順序の入れ替えが含まれます。`verbose` と `clean` のブールフラグが追加されました。極、残差、およびゼロ（`pol`, `res`, `zer`）は、`prz(z::AAAapprox)` を呼び出すことで必要に応じて計算されます。

注 2. コードは（ほぼ）`BigFloat` で動作します。`prz` が一般化されていないため、`BigFloat` を使用する場合は `clean=false` に設定してください。デフォルトの許容誤差が不十分な場合があるため、`tol` を明示的に小さな `BigFloat` 値として指定してください。

# 例

```julia
    using BaryRational
    xrat = [-1//1:1//100:1//1;];
    xbig = BigFloat.(xrat);
    fbig = sin.(xbig);
    sf = aaa(xbig, fbig, verbose=true, clean=false, tol=BigFloat(1/10^40));

    julia @v1.10> sin(BigFloat(-1//3))
    -0.3271946967961522441733440852676206060643014068937597915900562770705763744817618

    julia @v1.10> sf(BigFloat(-1//3))
    -0.3271946967961522441733440852676206060643014068937597915900562770705763744817662
```
