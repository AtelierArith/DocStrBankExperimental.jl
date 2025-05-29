```
Validator(T|subcon, validate) -> Validator{T}
```

`validate`関数に基づいてバリデーターを作成します。

# 引数

  * `subcon::Construct{T}`: 基本となる構造。
  * `validate`: バリデート関数。関数は`(::T; contextkw...)->Bool`のようなシグネチャを持つ必要があります。
