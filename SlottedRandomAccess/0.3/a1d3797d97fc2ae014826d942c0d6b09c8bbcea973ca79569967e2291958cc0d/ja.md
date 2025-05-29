```julia
struct RA4Step <: SlottedRandomAccess.FixedRepSlottedRAScheme{1}
```

4ステップRA手順を表す型で、RA競合期間（msg1）中にスロットALOHAが使用され、成功裏にデコードされたmsg1パケットが実際のデータのmsg3送信のために直交リソースを割り当てるために使用されます。

!!! note
    このRAスキームの型は、msg1のパケットデコードプロセスのみをシミュレートし、オプションでフレームごとの成功したパケットの最大数をmsg3送信に関連するスロットの数に制限します。


# フィールド

  * `msg1_occasions::Int64`: 各RAフレームでmsg1ランダムアクセスに割り当てられた時間の機会（スロット）の数。
  * `msg3_occasions::Int64`: 各RAフレームでmsg3送信に割り当てられた時間の機会（スロット）の数。
  * `freq_slots::Int64`: 各時間スロットで利用可能な周波数スロット（すなわちサブキャリア）の数。msg1とmsg3の送信に対してサブキャリアの数が同じであると仮定されています。
  * `limit_packets::Bool`: msg3送信に関連するスロットの数（すなわち`msg3_occasions * freq_slots`）にデコードされたパケットの最大数を制限するかどうかを指定するフラグ。

# コンストラクタ

```
RA4Step(msg1_occasions, msg3_occasions; freq_slots = 48, limit_packets = true)
```

## 例

以下のコードは、msg1に対して5つの時間の機会を、msg3に対して2つの時間の機会を持つ4ステップRAスキームを生成し、各時間スロットに対して20の周波数スロット（すなわちサブキャリア）を仮定し、各フレームでデコードされたパケットの最大数を実際のmsg3スロットの数（すなわち`2 * 20`）に制限します。

```julia-repl
julia> scheme = RA4Step(5, 2; freq_slots = 20, limit_packets = true)
```

参照: [`CRDSA`](@ref), [`MF-CRDSA`](@ref)
