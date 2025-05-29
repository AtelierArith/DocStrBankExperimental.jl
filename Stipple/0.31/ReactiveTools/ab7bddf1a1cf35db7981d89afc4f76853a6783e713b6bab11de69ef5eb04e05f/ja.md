```
@created(expr)
```

vue要素の`created`セクションのためのjsステートメントを定義します。

exprは次のいずれかです。

  * javascriptコードを含む`String`
  * javascriptコードの`String`を返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@created """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@created MyApp [startcamera, stopcamera]
```

結果の確認は次のように行えます。

```
julia> render(MyApp())[:created]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
