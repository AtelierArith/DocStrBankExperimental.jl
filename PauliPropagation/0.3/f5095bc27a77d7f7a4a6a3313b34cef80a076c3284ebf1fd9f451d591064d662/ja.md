```
applytoall!(gate, theta psum, output_psum; kwargs...)
```

`applymergetruncate!`の下にある2次関数で、1つのゲートを`psum`内のすべてのパウリ文字列に適用し、デフォルトで結果を`output_psum`に移動します。この関数の後、`psum`と`output_psum`に残っているパウリ文字列はマージされます。この関数は、低レベルの関数`applyandadd!`と`apply`が不十分な場合にカスタムゲートのためにオーバーライドできます。特に、この関数は、メモリの移動を減らすために`psum`と`output_psum`の両方を同時に操作するために使用できます。現在のパウリ文字列以外の`psum`を操作すると、エラーが発生する可能性が高いことに注意してください。カスタムゲートを定義する方法の例については、`4-custom-gates.ipynb`を参照してください。
