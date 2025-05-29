```
@activated(expr)
```

`activated` セクションの js ステートメントを vue 要素のために定義します。

expr は次のいずれかです。

  * JavaScript コードを含む `String`
  * JavaScript コードの `String` を返す `Function`
  * 上記の `Vector`

### 例 1

```julia
@activated """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@activated MyApp [startcamera, stopcamera]
```

結果を確認するには、次のようにします。

```
julia> render(MyApp())[:activated]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
