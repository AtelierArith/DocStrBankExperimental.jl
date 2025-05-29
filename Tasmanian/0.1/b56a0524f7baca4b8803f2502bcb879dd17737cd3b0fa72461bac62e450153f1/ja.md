```
setSurplusRefinement!(tsg::TasmanianSG, tol::Float64; output::Int=-1, refinement_type::AbstractString="", level_limits=Vector{Int32}(undef, 0), scale_correction = Vector{Float64}(undef, 0))
```

階層的な余剰を誤差指標として使用することで、余剰精緻化は精度を向上させるためにグリッドにポイントを追加します。

シーケンスグリッドを使用する場合: このアルゴリズムは、貪欲なナップサック問題に対応します。

ローカル多項式またはウェーブレットグリッドを使用する場合、この呼び出しはローカル空間精緻化に対応します。

許容誤差: float（非負）            相対誤差の許容誤差、すなわち、            余剰が許容誤差を超えるポイントに対してのみ            精緻化を行います。

出力: int（使用する出力を示す）          精緻化に使用する出力を選択します。          シーケンスおよびローカル多項式グリッドは -1 を受け入れ、          すべての出力を示します。

refinement_type: 階層的および方向精緻化戦略                  'classic'  'parents'   'direction'   'fds'   'stable'                  ローカル多項式およびウェーブレットグリッドにのみ適用可能です。

scale*correction: 非負の数の行列                   正規化された余剰を許容誤差と比較する代わりに、                   スケーリングされた余剰が使用されます。                   補正により、                   精緻化プロセスを手動で誘導できます。                   i 番目のポイントの j 番目の出力の余剰は                   scale*correction[i][j] によってスケーリングされます。                   scale*correction.shape[0] は                   getNumLoaded() と等しくなければなりません。                   空の場合、スケールは 1.0 と見なされます。                   scale*correction.shape[1] は、                   プロセスで使用される出力の数と等しくなければなりません。これは                   output == -1 の場合は getNumOutputs() と等しく、                   output > -1 の場合は 1 です。
