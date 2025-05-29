```
@destroyed(expr)
```

vue要素の`destroyed`セクションのためのjsステートメントを定義します。

exprは次のいずれかです。

  * javascriptコードを含む`String`
  * javascriptコードの`String`を返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@destroyed """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@destroyed MyApp [startcamera, stopcamera]
```

結果の確認は次のように行うことができます。

```
julia> render(MyApp())[:destroyed]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
