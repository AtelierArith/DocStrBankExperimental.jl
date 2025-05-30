AMDへの呼び出しに関連する制御と情報を保持するベースタイプ。`control`は次のコンポーネントを持つ`Vector{Float64}`です：

  * d = control[AMD_DENSE]: max(d√n, 16)エントリを超える行は「密」と見なされ、順列の最後に表示されます。

d < 0 の場合、どの行も密として扱われません。

  * control[AMD_AGGRESSIVE]: 非ゼロの場合、攻撃的な吸収をトリガーします。

`info`は順序に関する統計を含む`Vector{Float64}`です。
