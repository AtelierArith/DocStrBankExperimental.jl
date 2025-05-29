```
applyandadd!(gate, pstr, coefficient, theta, output_psum; kwargs...)
```

`applymergetruncate!`の下にある3番目のレベルの関数で、1つのゲートを`psum`内の1つのパウリ文字列に適用し、デフォルトで結果を`output_psum`に移動します。この関数は、下位レベルの関数`apply`が不十分な場合にカスタムゲート用にオーバーライドできます。これは、`apply`が一意の出力数を返さないために型安定性がない場合に起こる可能性が高いです。例えば、パウリゲートは1または2（pstr、coefficient）の出力を返します。カスタムゲートを定義する方法の例については、`4-custom-gates.ipynb`を参照してください。
