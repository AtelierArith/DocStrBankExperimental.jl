`buildbasis` メソッドは `Molecule` を入力として受け取り、私たちに `GaussianBasis` 型の配列を返します。例えば、同じ `h2.xyz` の例を開いてみましょう。標準基底セットとして、STO-3G データを使用します。

```julia
2 

H      -1.788131055      0.000000000     -4.028513155
H      -1.331928651      0.434077746     -3.639854078
```

ファイルを入力として与えます：

```julia
hydrogen = molecule("h2.xyz")
sto3g = buildbasis(hydrogen)
```
