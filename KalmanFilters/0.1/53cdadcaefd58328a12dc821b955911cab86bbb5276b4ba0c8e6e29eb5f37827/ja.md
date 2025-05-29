```julia
calc_nis_test(nis_values; num_measurements)

```

正規化イノベーション二乗 (NIS) テスト

両側有意性テスト、偽アラーム確率 α = 0.05

信頼区間 [r1 r2] を計算し、Prob{ ∑ NIS 値} ∈ [r1 r2] ∣ H*0 ) = 1 - α をテストします。仮説 H*0: N * ∑ NIS 値 ∼ χ^2_{dof}      dof (自由度): N * m (N: ウィンドウの長さ, m: 状態ベクトルの次元) については https://cs.adelaide.edu.au/~ianr/Teaching/Estimation/LectureNotes2.pdf を参照してください。
