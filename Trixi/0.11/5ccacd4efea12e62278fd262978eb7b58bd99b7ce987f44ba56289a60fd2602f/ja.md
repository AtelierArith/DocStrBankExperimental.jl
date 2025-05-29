```
AnalysisCallback(semi; interval=0,
                        save_analysis=false,
                        output_directory="out",
                        analysis_filename="analysis.dat",
                        extra_analysis_errors=Symbol[],
                        extra_analysis_integrals=())
```

数値解を `interval` タイムステップごとに分析し、結果を画面に表示します。`save_analysis` が `true` の場合、結果は `joinpath(output_directory, analysis_filename)` にも保存されます。

追加の誤差を計算することもできます。例えば、`extra_analysis_errors = (:l2_error_primitive, :linf_error_primitive)` または `extra_analysis_errors = (:conservation_error,)` を渡すことで可能です。

[`default_analysis_errors`](@ref) の計算を省略したい場合（計算時間を節約するため）、`analysis_errors = Symbol[]` を指定してください。注意: `default_analysis_errors` はすべての方程式に対して `:l2_error` と `:linf_error` です。`extra_analysis_errors` として `:conservation_error` のみを計算したい場合、すなわち `:l2_error, :linf_error` を含めずに計算したい場合は、`analysis_errors = [:conservation_error]` を指定する必要があります。

`extra_analysis_integrals` におけるさらなるスカラー関数 `func` は数値解に適用され、計算領域全体で積分されます。これに関するいくつかの例は [`entropy`](@ref)、[`energy_kinetic`](@ref)、[`energy_internal`](@ref)、および [`energy_total`](@ref) です。また、上記の例と同じシグネチャを持つ独自の関数を作成し、`extra_analysis_integrals` を介して渡すこともできます。カスタム分析量を作成する方法については、`Trixi.analyze`、`Trixi.pretty_form_utf`、および `Trixi.pretty_form_ascii` に関する開発者コメントを参照してください。

さらに、分析コールバックは、総実行時間、パフォーマンスインデックス（時間/DOF/rhs!）、ガーベジコレクション（GC）に費やした時間、または現在のメモリ使用量（割り当てられたメモリ）など、計算性能を評価するのに役立ついくつかの量を記録し出力します。
