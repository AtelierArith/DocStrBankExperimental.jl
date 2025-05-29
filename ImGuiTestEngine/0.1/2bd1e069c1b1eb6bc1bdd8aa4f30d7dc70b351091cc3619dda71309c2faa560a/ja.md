```julia
DestroyContext(engine::ImGuiTestEngine.Engine; throw)

```

テストエンジンコンテキストを破棄します。

# 引数

  * `throw=true`: エンジンがすでに破棄されている場合に例外をスローするかどうか。

# 例

```julia
engine = te.CreateContext()
te.DestroyContext(engine)
```
