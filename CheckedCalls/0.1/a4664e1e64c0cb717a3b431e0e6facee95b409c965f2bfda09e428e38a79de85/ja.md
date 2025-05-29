```
struct ReturnValueContainsNaN <: Exception
```

関数 `f` の戻り値 `r` が引数 `args` で呼び出されたときに `NaN` 値であるか、または `NaN` 値を含む場合にスローされる例外です。

コンストラクタ:

```julia
ReturnValueContainsNaN(r, f, args)
ReturnValueContainsNaN(r, f, args, cause)
```

`cause` はデフォルトで `missing` ですが、`NaN` 値の原因を示す任意のものに設定することができます。これには、`f(args...)` を計算中に遭遇した別の `ReturnValueContainsNaN` インスタンスが含まれます。
