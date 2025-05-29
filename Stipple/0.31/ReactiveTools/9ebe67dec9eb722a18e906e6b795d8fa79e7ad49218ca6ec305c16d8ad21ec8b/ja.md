```
@updated(expr)
```

vue要素の`updated`セクションのためのjsステートメントを定義します。

exprは次のいずれかです。

  * javascriptコードを含む`String`
  * javascriptコードの`String`を返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@updated """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@updated MyApp [startcamera, stopcamera]
```

結果を確認するには、次のようにします。

```
julia> render(MyApp())[:updated]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
