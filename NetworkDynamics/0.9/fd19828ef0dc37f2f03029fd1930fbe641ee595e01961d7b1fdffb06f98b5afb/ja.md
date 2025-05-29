```
@obsex([name =] expression)
```

観測可能な式を定義します。これは、既知の状態/パラメータ/観測可能量の単純な組み合わせです。`@obsex(...)`は、シンボリックインデックスとして使用できる`ObservableExpression`を返します。これは、2成分の複素状態の引数など、一般的な「導出」変数の迅速なプロットやエクスポートを主に目的としています。例えば：

```
sol(t; idxs=@obsex(arg = atan(VIndex(1,:u_i), VIndex(1,:u_r))))
sol(t; idxs=@obsex(δrel = VIndex(1,:δ) - VIndex(2,:δ)))
```
