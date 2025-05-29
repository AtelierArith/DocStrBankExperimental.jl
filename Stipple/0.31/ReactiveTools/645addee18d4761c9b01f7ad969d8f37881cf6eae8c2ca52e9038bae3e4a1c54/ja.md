```
@mounted(expr)
```

vue要素の`mounted`セクションのためのjsステートメントを定義します。

exprは次のいずれかです。

  * javascriptコードを含む`String`
  * javascriptコードの`String`を返す`Function`
  * 上記の`Vector`

### 例 1

```julia
@mounted """
    if (this.cameraon) { startcamera() }
"""
```

### 例 2

```julia
startcamera() = "if (this.cameraon) { startcamera() }"
stopcamera() = "if (this.cameraon) { stopcamera() }"

@mounted MyApp [startcamera, stopcamera]
```

結果の確認は次のように行うことができます。

```
julia> render(MyApp())[:mounted]
JSONText("function(){
    if (this.cameraon) { startcamera() }

    if (this.cameraon) { stopcamera() }
}")
```
