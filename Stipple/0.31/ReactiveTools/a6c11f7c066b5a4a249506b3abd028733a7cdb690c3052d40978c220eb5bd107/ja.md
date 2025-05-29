```
@before_update(expr)
```

vue要素の`beforeUpdate`セクションのためのjsステートメントを定義します。

exprは次のいずれかです。

  * javascriptコードを含む`String`
  * javascriptコードのStringを返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@before_update """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@before_update MyApp [startcamera, stopcamera]
```

結果の確認は次のように行えます。

```
julia> render(MyApp())[:beforeUpdate]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
