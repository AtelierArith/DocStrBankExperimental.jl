```
iddata(y,       Ts = nothing)
iddata(y, u,    Ts = nothing)
iddata(y, u, x, Ts = nothing)
```

**時間領域**の同定データオブジェクトを作成します。

# 引数

  * `y::AbstractArray`: 出力データ（必須）
  * `u::AbstractArray`: 入力データ（利用可能な場合）
  * `x::AbstractArray`: 状態データ（利用可能な場合）
  * `Ts::Union{Real,Nothing} = nothing`: オプションのサンプル時間

時系列が多変量の場合、時間は*最後の*次元にあり、配列のサイズは`(num_variables, num_timepoints)`です（以下の例を参照）。

# iddataに対する操作

  * [`detrend`](@ref)
  * [`prefilter`](@ref)
  * [`resample`](@ref)
  * 時間次元に沿って2つを追加 `[d1 d2]`（`d1`の終わりのシステムの状態が`d2`の始まりの状態に近い場合のみ実行）
  * 時系列をインデックス `d[output_index, input_index]`
  * 時間軸をインデックスで指定 `d[time_indices]`
  * 秒で時間軸をインデックス `d[3Sec:12Sec]` (`using ControlSystemIdentification: Sec`)
  * 入力、出力、サンプル時間の数にアクセス: `d.nu, d.ny, d.Ts`
  * 時間ベクトルにアクセス `d.t`
  * 出力をスケールするために前乗算 `C * d`。異なる大きさを持つ場合、モデルを推定する前に複数出力システムの出力をほぼ同じサイズにスケーリングすることが推奨されます。
  * 入力をスケールするために後乗算 `d * B`
  * [`writedlm`](@ref)
  * [`ramp_in`](@ref), [`ramp_out`](@ref)
  * `plot`
  * [`specplot`](@ref)
  * [`crosscorplot`](@ref)

# 例

```jldoctest
julia> iddata(randn(10))
出力データの長さ10、1出力、Ts = nothing

julia> iddata(randn(10), randn(10), 1)
入力出力データの長さ10、1出力、1入力、Ts = 1

julia> d = iddata(randn(2, 10), randn(3, 10), 0.1)
入力出力データの長さ10、2出力、3入力、Ts = 0.1

julia> [d d] # 時間に沿って連結
入力出力データの長さ20、2出力、3入力、Ts = 0.1

julia> d[1:3]
入力出力データの長さ3、2出力、3入力、Ts = 0.1

julia> d.nu
3

julia> d.t # 時間ベクトルにアクセス
0.0:0.1:0.9
```

# 複数データセットの使用

いくつかの推定方法は、モデルを推定するために複数のデータセットの使用をサポートしています。この場合、データセットはiddataオブジェクトのベクトルとして提供されます。現在これをサポートしている方法は次のとおりです。

  * [`arx`](@ref)
  * [`era`](@ref)

他のいくつかの推定方法は、軽微な修正で複数のデータセットを受け入れるようにすることができます。

いくつかの状況では、複数のデータセットは連結によっても処理できます。これが良いアイデアであるためには、1つのデータセットの終わりのシステムの状態が次のデータセットの始まりの状態に近い必要があります。たとえば、すべての実験は同じ動作点で開始し、終了します。
