```
@before_mount(expr)
```

vue要素の`beforeMount`セクションのためのjsステートメントを定義します。

exprは以下のいずれかです。

  * javascriptコードを含む`String`
  * javascriptコードのStringを返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@before_mount """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@before_mount MyApp [startcamera, stopcamera]
```

結果の確認は以下の方法で行えます。

```
julia> render(MyApp())[:beforeMount]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
