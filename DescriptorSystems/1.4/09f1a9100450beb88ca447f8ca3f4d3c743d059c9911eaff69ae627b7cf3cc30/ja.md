```
r = rtf(f; Ts = rts, var = rvar)
```

有理伝達関数 `r(λ) = f(λ)` をサンプリング時間 `rts` と変数名 `rvar` で作成します。次のようにします：

(1) `f(λ)` が有理伝達関数である場合、`r.Ts = rts`（デフォルトは `rts = f.Ts`）および `r.var = rvar`（デフォルトは `rvar = f.var`）となります。

(2) `f(λ)` が有理関数である場合、`r.Ts = rts`（デフォルトは `rts = 0`）および `r.var = rvar`（デフォルトは `rvar = Polynomials.indeterminate(f.num)`）となります。

(3) `f(λ)` が多項式である場合、`r.Ts = rts`（デフォルトは `rts = 0`）および `r.var = rvar`（デフォルトは `rvar = Polynomials.indeterminate(f)`）となります。

(4) `f(λ)` が実数または複素数である場合、`r.Ts = rts`（デフォルトは `rts = 0`）および `r.var = rvar`（デフォルトは `rvar = :s`）となります。
