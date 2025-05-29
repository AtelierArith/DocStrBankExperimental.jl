```
IterModeは、利益分配メカニズムの反復的な特定のモダリティを定義する構造体です
```

## フィールド

player*set     プレイヤーのベクトル callback*benefit*by*coalition : 関数     連合の利益と連合の総利益を決定するために使用されるコールバック関数 callback*worst*coalition : 関数     最悪の利益を持つ連合と連合の総利益を決定するために使用されるコールバック関数。     引数は次のようにする必要があります:     - (必須) 現在の報酬分配をユーザーごとに説明するDictのようなコンテナ     - kwargs (オプション):         - modify*solver*options: 最適化コールバックを反復的に変更するためのペアのベクトル             計算時間を短縮するために。 実装されたコールバックは次のとおりです:             1. best*obj*stop: best*obj*stopコールバックが反復法で使用されるとき、                 対応するオプションはここで値に応じて更新されます             2. lower*relaxation*stop*option: 下限に達したときに実行を停止するオプション     関数は、各エントリoが次の内容を含むNamedTupleのベクトルを返す必要があります:     - least*profitable*coalition: 結果oの最悪の連合のメンバー     - coalition*benefit: 結果oの連合の利益     - min_surplus: 結果oの連合の最小余剰
