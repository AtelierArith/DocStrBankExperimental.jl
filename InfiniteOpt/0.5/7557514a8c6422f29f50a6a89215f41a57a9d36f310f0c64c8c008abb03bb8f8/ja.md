```
call_function(fref::GeneralVariableRef, support...)::Float64
```

`fref`のパラメータ関数を`support`で呼び出します。`fref`がパラメータ関数でない場合、`ArgumentError`がスローされます。
