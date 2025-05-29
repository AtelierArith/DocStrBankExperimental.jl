```
SolutionCertificate
```

単一の解に対する[`certify`](@ref)の結果。初期解を含み、認証が成功した場合は真の解が含まれる複素数区間のベクトルが含まれます。複素数区間は`Arblib.AcbMatrix`として与えられます。`Arblib.AcbMatrix`は`Arblib`のデフォルト形式で印刷されます。これは、区間の中点が十分な正確な桁数で表現できない場合、`Arblib`は中点を印刷しないことを意味します。代わりに、`r`がボールの絶対値の上限である形の区間`[+/- r]`が印刷されます。正しい区間の囲いは次のように印刷できます。

```julia
Base.show(certificate::SolutionCertificate; digits = 16, more = true)
```

これは、`16`桁で`Flint`の[`ARB_STR_MORE`](https://flintlib.org/doc/arb.html#c.arb_get_str)機能を使用します。
