autoexogenize!(plan, model, date)

与えられたモデルで定義された「autoexogenize」プロトコルに従って、与えられた計画を修正します。自動外生化リスト内のすべての変数は内生的になり、それに対応するショックは与えられた日付または範囲にわたって外生的になります。`date`は、時点（与えられた計画と同じ頻度）、範囲、反復可能なもの、またはコンテナであることができます。
