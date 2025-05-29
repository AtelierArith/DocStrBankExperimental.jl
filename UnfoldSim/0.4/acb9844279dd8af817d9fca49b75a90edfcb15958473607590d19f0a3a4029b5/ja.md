```
hrf(;
TR = 1,
peak = 6.0,
post_undershoot = 16,
length = 32.0,
peak_width = 1.0,
post_undershoot_width = 1,
amplitude = 6,
shift = 0)

パラメータ化されたBOLD血行動態反応関数（HRF）カーネルをガンマ関数に基づいて生成します。

実装とデフォルトパラメータはSPMツールボックスから取得されました。

注意: TR = 1/sfreq

# キーワード引数

  * `TR = 1`: 繰り返し時間、1/sfreq。
  * `length = 32.0`: カーネルの合計長（秒）。
  * `amplitude = 6`: 最大振幅。
  * `peak = 6.0`: ピークのタイミング。
  * `peak_width = 1.0`: ピークの幅。
  * `post_undershoot = 16`: ポストアンダーシュートのタイミング。
  * `post_undershoot_width = 1`: ポストアンダーシュートの幅。
  * `shift = 0`: HRF全体をシフトします。

# 戻り値

  * `Vector`: HRF BOLD応答。

# 例

```

julia-repl julia> hrf() 33-element Vector{Float64}:   0.0   0.0007715994433635659   0.019784004131204957   0.08202939459091822   0.158157713522699   ⋮  -0.0006784790038792572  -0.00042675060451877775  -0.000263494738348278  -0.00015990722628360688  -9.548780093799345e-5 ```
