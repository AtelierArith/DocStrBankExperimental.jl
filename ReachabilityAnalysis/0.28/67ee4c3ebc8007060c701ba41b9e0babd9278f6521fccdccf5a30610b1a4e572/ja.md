```
homogenize(ivp::IVP{<:CLCCS{N,MTA,MTB,XT,UT},ST}) where {N, MTA<:AbstractMatrix{N},
    MTB<:IdentityMultiple{N}, XT<:LazySet{N}, UT<:ConstantInput{<:Singleton{N}}, ST<:LazySet{N}}
```

非同次線形初期値問題を補助状態変数を導入することによって同次のものに変換します。

### 入力

  * `ivp` – 初期値問題

### 出力

同次初期値問題。

### 注意事項

この関数は、$x' = Ax + u$、$x ∈ X$ で $u(0) ∈ U = {u}$（単一要素）を持つ標準的な初期値問題を、入力のない同次問題 $y' = Â * y$、$y ∈ Y$ に変換します。
