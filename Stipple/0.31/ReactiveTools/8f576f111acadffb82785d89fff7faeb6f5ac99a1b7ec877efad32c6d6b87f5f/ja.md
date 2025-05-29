```
@before_create(expr)
```

vue要素の`beforeCreate`セクションのためのjsステートメントを定義します。

exprは次のいずれかです。

  * javascriptコードを含む`String`
  * javascriptコードのStringを返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@before_create """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@before_create MyApp [startcamera, stopcamera]
```

結果の確認は次のように行うことができます。

```
julia> render(MyApp())[:beforeCreate]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
