```
@jkernel kerneldef, [kernelname, [accelname, ]][clauses...]
```

カーネルコンテキストを作成します。

`kernelname` または `accelname` が指定されていない場合、現在アクティブな accel またはカーネルコンテキストが使用されます。

# 引数

  * `kerneldef`::String: Jai カーネル定義
  * `kernelname`::String: カーネルコンテキスト名
  * `accelname`::String: アクセルコンテキスト名

他にも [`@jaccel`](@jaccel)、[`@jenterdata`](@jenterdata) を参照してください。

# 例

```julia-repl
julia> @jkernel knlfilepath mykernel myaccel
0
```

# 実装

T.B.D.
