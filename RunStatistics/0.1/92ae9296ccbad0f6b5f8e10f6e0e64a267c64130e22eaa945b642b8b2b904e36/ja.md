```
squares_pvalue_approx(T_obs::Real, L::Integer, [epsp::Real])
```

`T_obs`に対して`L`の条件下でのP(T >= `T_obs`)の近似値、すなわち、データで観測されたSquares統計量`T`が`T_obs`以上である確率のp値を計算します。データポイントの総数は`L = n * N`であり、特に定義されていない場合、関数はデフォルト値`N = 80`および`n = L / N`を選択します。

`N`と`n`の特定の選択を指定するには、次のようにします：

```
squares_pvalue_approx(T_obs::Real, Ns::AbstractArray,  [epsp::Real])
```

ここで、`Ns`は`N::Integer`と`n::Real`を最初と二番目の要素として持つ配列です：Ns = [N, n]

精度の下限は`n * 10^(-14)`であり、この境界までの望ましい精度はオプションの`epsp`引数で指定できます。精度に関する詳細は`Guide/Details of computation`のドキュメントを参照してください。

この関数は、次の文献の式(17)を実装しています：

Frederik Beaujean and Allen Caldwell. *Is the bump significant? An axion-search example*

https://arxiv.org/abs/1710.06642
