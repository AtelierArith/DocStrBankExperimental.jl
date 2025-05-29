```
r = rtf(var; Ts = rts)
r = rtf('s') or r = rtf('z'; Ts = rts) 
r = rtf("s") or r = rtf("z"; Ts = rts) 
r = rtf(:s) or r = rtf(:z; Ts = rts)
```

ラショナル伝達関数 `r(λ) = λ` を作成します。ここで、`r.var` と `r.Ts` は次のように設定されます：

```
(1) `r.var = :s` かつ `r.Ts = 0` もし `var = 's'`、または `var = "s"` または `var = :s` の場合；

(2) `r.var = :z` かつ `r.Ts = rts` もし `var = 'z'`、または `var = "z"` または `var = :z` の場合；

(3) `r.var = var` かつ `r.Ts = rts` （デフォルト `rts = 0.`）それ以外の場合。
```
