```
AnalysisCallback(semi; interval=0,
                       extra_analysis_errors=Symbol[],
                       extra_analysis_integrals=(),
                       io=stdout)
```

数値解を毎 `interval` タイムステップごとに分析します。各コンポーネントのL2ノルムとL∞ノルムはデフォルトで計算されます。追加の誤差は、例えば `extra_analysis_errors = (:conservation_error,)` を渡すことで計算できます。

`extra_analysis_integrals` にあるさらなるスカラー関数 `func` は数値解に適用され、計算領域全体で積分されます。これに関するいくつかの例は [`entropy`](@ref) と [`energy_total`](@ref) です。上記の例と同じシグネチャを持つ独自の関数を作成し、`extra_analysis_integrals` を介して渡すこともできます。計算された誤差と積分は各タイムステップごとに保存され、[`errors`](@ref) および [`integrals`](@ref) を呼び出すことで取得できます。

シミュレーション中、`AnalysisCallback` は `io` に情報を出力します。
