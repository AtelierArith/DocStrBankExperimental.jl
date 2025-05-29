```
Options(;   mag_combine=:SNR,
            mag_sens=nothing,
            mag_softplus=true,
            phase_unwrap=:laplacian,
            phase_hp_sigma=[4,4,0],
            phase_scaling_type=:tanh,
            phase_scaling_strength=4,
            writesteps=nothing)
```

  * `mag_combine` は大きさのエコーの組み合わせを選択します。オプションは 

      * `:SNR`
      * `:average`
      * `:last` は最後のエコーを選択します
      * `(:CNR => (:gm, :wm))` は、現在7Tでのみ動作する `src/tissue.jl` で選択可能な組織クラスの間のコントラストを最適化します
      * `(:echo => 3)` は3番目のエコーを選択します
      * `(:closest => 15.3)` は15.3 msに最も近いエコーを選択します
      * `(:SE => 15.3)` は15.3 msのエコー時間を使用した対応する単一エコースキャンで達成されるコントラストをシミュレートします。
  * `mag_sens` が配列に設定されている場合、CLEAR-SWI感度推定の代わりに使用されます。これは `mag_sens=[1]` に設定して、感度補正を実質的に回避するための定数感度1を使用することもできます。期待されるバイアスフィールドサイズのsigma*mm値を変更するには、例えば `mag*sens=(:sigma_mm => 7)` に設定します。デフォルトは7mmです。
  * ソフトプラス関数で結合された大きさのスケーリングを無効にするには、`mag_softplus=false` を使用します。
  * `phase_unwrap` は `:laplacian`、 `:romeo`、または `:laplacianslice`（スライスごとのラプラシアンアンラッピング）です。
  * `phase_hp_sigma` はハイパスフィルタリングに使用され、[x,y,z]次元のボクセルで指定されます。
  * `phase_scaling_type` は位相マスクを作成するためのスケーリング関数で、`：tanh` または `：negativetanh`（シグモイドフィルタリング用）、または `：positive`、 `：negative`、 `：triangular`（従来のSWIアプリケーション用）です。
  * `phase_scaling_strength` は作成された位相マスクの強度を調整します。より高い `phase_scaling_strength` はより強い位相の外観を持ちます。従来のSWI `phase_scaling_type` では、位相マスクの乗算の数またはパワーに対応します。
  * `writesteps` を中間ステップを保存するパスに設定します。例： `writesteps="/tmp/clearswi_steps"`。 `nothing` に設定すると、中間ステップは保存されません。
  * `qsm` を true に設定します。
