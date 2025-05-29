```
@kwmethod expr
```

キーワードメソッドをディスパッチのために定義します。`expr` はキーワード引数ブロック（空である可能性があります）を持つ標準的な関数定義（ブロックまたはインラインのいずれか）である必要があります。

位置引数のシグネチャは、最初に [`@kwdispatch`](@ref) マクロによって指定される必要があります。

# 例

```julia
@kwdispatch f() # 位置引数なしの形式を指定

@kwmethod f(;) = nothing # キーワード引数なし
@kwmethod f(;a) = a
@kwmethod f(;b) = 2*b
@kwmethod f(;a,b) = a+2*b
```
