```
@code_typed
```

関数またはマクロ呼び出しの引数を評価し、それらの型を決定し、結果の式に対して[`code_typed`](@ref)を呼び出します。オプション引数`optimize`を使用して

```
@code_typed optimize=true foo(x)
```

インライン化などの追加最適化が適用されるかどうかを制御します。
