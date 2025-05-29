`parsebasis` メソッドは XYZ ファイルを受け取り、`GaussianBasisSet` オブジェクトのリストを返します。XYZ ファイルは、最初の行に原子の数が含まれ、その後に各原子の原子記号とカルテシアン座標が続くシンプルなテキストファイルです。例えば、以下は水分子の XYZ ファイルです：

```julia
3

O 0.000000 -0.007156 0.965491
H 0.000000 0.001486 -0.003471
H 0.000000 0.931026 1.207929
```

ファイルを入力として与えます：

```julia
621g = parsebasis("../test/data/water/water.xyz", "6-21g")
```

そして、次のような結果が得られます：

```julia
Main.BasisSets.GaussianBasisSet[
    Main.BasisSets.GaussianBasisSet(
        [5472.27 817.806 186.446 53.023 17.18 5.91196], 
        [0.00183216881 0.01410469084 0.06862615542 0.229375851 0.466398697 0.3641727634], 
        0, 0, 0
    ), 
    Main.BasisSets.GaussianBasisSet([7.40294 1.5762], [-0.4044535832 1.221561761], 0, 0, 0), 
    Main.BasisSets.GaussianBasisSet([7.40294 1.5762], [0.244586107 0.8539553735], 1, 0, 0), 
    Main.BasisSets.GaussianBasisSet([7.40294 1.5762], [0.244586107 0.8539553735], 0, 1, 0), 
    Main.BasisSets.GaussianBasisSet([7.40294 1.5762], [0.244586107 0.8539553735], 0, 0, 1), 
    Main.BasisSets.GaussianBasisSet([0.373684;;], [1.0;;], 0, 0, 0), 
    Main.BasisSets.GaussianBasisSet([0.373684;;], [1.0;;], 1, 0, 0), 
    Main.BasisSets.GaussianBasisSet([0.373684;;], [1.0;;], 0, 1, 0), 
    Main.BasisSets.GaussianBasisSet([0.373684;;], [1.0;;], 0, 0, 1), 
    Main.BasisSets.GaussianBasisSet([5.447178 0.82454724], [0.1562849787 0.9046908767], 0, 0, 0), 
    Main.BasisSets.GaussianBasisSet([0.18319158;;], [1.0;;], 0, 0, 0), 
    Main.BasisSets.GaussianBasisSet([5.447178 0.82454724], [0.1562849787 0.9046908767], 0, 0, 0), 
    Main.BasisSets.GaussianBasisSet([0.18319158;;], [1.0;;], 0, 0, 0)
]
```
