```
AbstractState_specify_phase(handle::Clong, phase::AbstractString)
```

すべてのさらなる計算に使用するフェーズを指定します。

# 引数

  * `handle`: メモリに保存されている状態クラスの整数ハンドル
  * `phase`: 使用するフェーズの文字列。可能な候補は以下に示されています：

| フェーズ名                      |             条件 |
|:-------------------------- | --------------:|
| phase_liquid               |                |
| phase_gas                  |                |
| phase_twophase             |                |
| phase_supercritical        |                |
| phase*supercritical*gas    | p < pc, T > Tc |
| phase*supercritical*liquid | p > pc, T < Tc |
| phase*critical*point       | p = pc, T = Tc |
| phase_unknown              |                |
| phase*not*imposed          |                |

# 例

```julia
julia> heos = AbstractState_factory("HEOS", "Water");
# 非常に低密度の状態点でフラッシュコールを行う、確実に蒸気
julia> @time AbstractState_update(heos, "DmolarT_INPUTS", 1e-6, 300);
  0.025233 秒 (5.23 k アロケーション: 142.283 KB)
# フェーズを指定する - 一部の入力（特に密度-温度）に対して、これは
# 飽和境界をチェックせずに状態方程式のより直接的な評価をもたらします
julia> AbstractState_specify_phase(heos, "phase_gas");
# もう一度試してみる - 少し速く
julia> @time AbstractState_update(heos, "DmolarT_INPUTS", 1e-6, 300);
  0.000050 秒 (5 アロケーション: 156 バイト)
julia> AbstractState_free(heos);
```
