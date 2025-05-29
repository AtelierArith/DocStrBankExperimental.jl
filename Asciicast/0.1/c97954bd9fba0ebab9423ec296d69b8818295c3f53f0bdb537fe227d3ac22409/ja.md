```
@cast_str(code_string, delay=0, allow_errors=false) -> Cast
```

`code_string`内のコードをREPLのような環境で実行することによって、[`Cast`](@ref)オブジェクトを作成します。

## 例

```julia
using Asciicast

c = cast"x=1"0.25 # ここで遅延を0.25に設定しています

Asciicast.save("test.cast", c)
```

例外を許可するには、文字列に対してマクロを手動で呼び出す必要があります：

```julia
using Asciicast
c = @cast_str("error()", 0, true)
Asciicast.save("test.cast", c)
```
