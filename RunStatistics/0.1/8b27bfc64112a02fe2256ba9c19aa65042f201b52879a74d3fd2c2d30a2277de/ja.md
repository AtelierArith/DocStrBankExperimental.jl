squares*cdf*approx(T_obs::Real, L::Integer, [epsp::Real])

`T_obs`でのSquares検定統計量の累積分布関数の値、すなわちデータで観測されたSquares統計量の値に対して、P(T < `T_obs` | `L = n * N`)の近似を計算します。データポイントの総数は`L = n * N`であり、特に定義されていない場合、関数はデフォルト値`N = 80`および`n = L / N`を選択します。

`N`と`n`の特定の選択を指定するには、次のようにします：

```
squares_cdf_approx(T_obs::Real,  Ns::AbstractArray, epsp::Real = 0)
```

ここで、`Ns`は`N::Integer`と`n::Real`を最初と二番目の要素として持つ配列です：Ns = [N, n]。

精度の下限は`n * 10^(-14)`であり、この境界までの望ましい精度はオプションの`epsp`引数で指定できます。精度に関する詳細は`Guide/Details of computation`のドキュメントを参照してください。

この関数は次の文献の式(17)を実装しています：

Frederik Beaujean and Allen Caldwell. *Is the bump significant? An axion-search example*

https://arxiv.org/abs/1710.06642
