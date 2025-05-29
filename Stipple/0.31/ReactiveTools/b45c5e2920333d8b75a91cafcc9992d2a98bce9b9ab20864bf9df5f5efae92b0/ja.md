```
@before_destroy(expr)
```

vue要素の`beforeDestroy`セクションのためのjsステートメントを定義します。

exprは以下のいずれかであることができます。

  * javascriptコードを含む`String`
  * javascriptコードのStringを返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@before_destroy """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@before_destroy MyApp [startcamera, stopcamera]
```

結果の確認は以下の方法で行うことができます。

```
julia> render(MyApp())[:beforeDestroy]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
