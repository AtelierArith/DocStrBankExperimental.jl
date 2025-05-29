```
toarray(lv::LabeledValues)
```

`toarray(...)` と `fromarray(...)` は、`LabeledValues` を Float64 のベクトルを引数に取る関数と互換性を持たせるための一対の関数です。これは非線形最適化関数に一般的です。 `toarray(lv)` は `LabeledValues` を受け取り、Float64 の順序付きベクトルを返します。 `fromarray(f,lv)` は少し微妙で、`g(toarray(lv)) = f(lv)` となる関数 `g` を返します。つまり、`fromarray(...)` を使用すると、`f(lv)` をベクトル引数を期待する関数への引数として使用することができます。
