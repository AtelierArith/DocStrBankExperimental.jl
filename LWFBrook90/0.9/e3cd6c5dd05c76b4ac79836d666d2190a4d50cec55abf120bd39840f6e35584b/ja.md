```
setup(parametrizedSPAC::SPAC;
    requested_tspan = nothing,
    soil_output_depths_m::Vector = zeros(Float64, 0))
```

SPACモデルの定義を受け取り、DifferentialEquations.jlパッケージによって解決可能なODEのシステムに離散化します。

必要に応じて、土壌の計算グリッドは特定の深さで値を出力するように細分化されます。例えば、`setup(SPAC; soil_output_depths_m = [-0.35, -0.42, -0.48, -1.05])`のように行います。

引数`requested_tspan`は、基準日からの開始日と終了日を含むタプルでシミュレーションの期間を定義します：`setup(SPAC; requested_tspan = (0,150))`。あるいは、2つのDataTimeのタプルとしても指定できます。`SPAC.reference_date`によって与えられる基準日は日0を指します。さらに、0から始まらないtspanを提供することも可能で、例えば(120,150)のように指定できます。その場合、初期条件はtspan[1]に適用されますが、大気強制は正しく考慮されます。
