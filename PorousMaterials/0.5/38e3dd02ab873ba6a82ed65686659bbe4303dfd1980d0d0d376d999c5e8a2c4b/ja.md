```
fluid = PengRobinsonFluid(fluid)
```

流体のプロパティ .csv ファイル `joinpath(PorousMaterials.rc[:paths][:data], "PengRobinson_fluid_props.csv")` から `fluid::Symbol` の臨界温度、臨界圧力、およびアセンチック因子を読み込み、完全な `PengRobinsonFluid` データ構造を返します。 **注意: PengRobinson*fluid*props.csv の最後の3行のコメントを削除しないでください。**

# 引数

  * `fluid::Symbol`: PengRobinsonFluid 構造体を構築したい流体分子

# 戻り値

  * `PengRobinsonFluid::struct`: Peng-Robinson 流体パラメータを含むデータ構造。
