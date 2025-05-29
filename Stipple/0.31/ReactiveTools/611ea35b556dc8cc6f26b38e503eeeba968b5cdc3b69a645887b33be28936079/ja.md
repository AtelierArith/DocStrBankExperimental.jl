```
@error_captured(expr)
```

vue要素の`errorCaptured`セクションのためのjsステートメントを定義します。

exprは以下のいずれかであることができます。

  * javascriptコードを含む`String`
  * javascriptコードのStringを返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@error_captured """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@error_captured MyApp [startcamera, stopcamera]
```

結果の確認は以下の方法で行うことができます。

```
julia> render(MyApp())[:errorCaptured]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
