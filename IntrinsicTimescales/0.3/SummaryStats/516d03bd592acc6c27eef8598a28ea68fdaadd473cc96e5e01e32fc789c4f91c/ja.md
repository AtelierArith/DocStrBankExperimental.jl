```
bat_integrated_autocorr_len(
    v::AbstractVectorOfSimilarVectors{<:Real};
    c::Integer = 5, tol::Integer = 50, strict = true
)
```

変数系列 `v` の統合自己相関長を推定します。

  * `c`: ウィンドウ探索のステップサイズ。
  * `tol`: 推定を信頼するために必要な最小自己相関時間数。
  * `strict`: 結果が信頼できない場合に例外をスローします。

この推定は、[Sokalのノート](http://www.stat.unc.edu/faculty/cji/Sokal.pdf)の16ページに記載されている反復手順を使用して、合理的なウィンドウサイズを決定します。

MITライセンスの下で、emcee PythonパッケージからJuliaに移植されました。元の著者はDan Foreman-Mackeyらです。
