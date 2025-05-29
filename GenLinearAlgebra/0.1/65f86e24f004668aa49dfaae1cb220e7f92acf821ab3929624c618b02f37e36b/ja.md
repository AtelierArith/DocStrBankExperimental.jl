GenLinearAlgebra: 任意の体および環における線形代数

Juliaの線形代数パッケージは一般的な数学パッケージには適していません：それは体が実数または複素数であると仮定し、近似計算を行うために浮動小数点を使用します。例えば、可逆な有理行列 `[1//(n+m) for  n in 1:11, m  in 1:11]` は `LinearAlgebra` において `rank` が10で、`Float64` のヌル空間の次元は1です。

ここでは、任意の体（または時には任意の環）で動作し、正確な計算を仮定する関数に興味があります。

詳細については、`echelon!, rowspace, independent_rows, in_rowspace, intersect_rowspace, lnullspace, GenLinearAlgebra.nullspace, GenLinearAlgebra.rank, solutionmat, charpoly, comatrix, permanent, symmetric_power, exterior_power, ratio, diagconj_elt, transporter, bigcell_decomposition, traces_words_mats, all_ge_1` のヘルプ文字列を参照してください。
