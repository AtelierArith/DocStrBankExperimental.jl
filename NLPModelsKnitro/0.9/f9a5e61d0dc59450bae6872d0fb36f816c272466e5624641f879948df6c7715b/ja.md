```
KnitroSolver(::Val{Bool}, nlp; kwargs...,)
```

`nlp`を`knitro!`で解くための`KnitroSolver`構造体を返します。

Knitroは境界以外の制約を持つ最小二乗問題を受け付けません。NLSModelに境界以外の制約がある場合、FeasibilityFormNLSに変換します。最初の引数は、問題が変換された場合は`Val(false)`、そうでない場合は`Val(true)`です。

可能な`kwargs`については、`knitro`を参照してください。
