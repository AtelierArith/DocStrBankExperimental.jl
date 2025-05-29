```
r = rtf(num, den; Ts = rts, var = rvar )
```

多項式 `num(λ)` と `den(λ)`、サンプリング時間 `rts`、および変数名 `rvar` を使用して、合理的な伝達関数 `r(λ) = num(λ)/den(λ)` を作成します。これは、次の形式の単一入力単一出力システムの伝達関数を表します。

```
Y(λ) = r(λ) U(λ),
```

ここで、`U(λ)` と `Y(λ)` はそれぞれ入力 `u(t)` と出力 `y(t)` のラプラス変換または `Z` 変換されたものであり、`λ = s` はラプラス変換における複素変数で、`rts = 0` の場合、または `λ = z` は `Z` 変換における複素変数で、`rts ≠ 0` の場合です。`num` と `den` は実数または複素数であることもできます。

結果として得られる `r` は `r.Ts = rts`（デフォルトは `rts = 0`）および `r.var = rvar` となります。`rvar` のデフォルト値は、`num` が多項式の場合は `rvar = Polynomials.indeterminate(num)`、`num` が数で `den` が多項式の場合は `rvar = Polynomials.indeterminate(den)`、両方が数の場合は `rvar = :s` です。
