2つの属性付き $C$-セット間のすべてのホモモルフィズムをバックトラッキング検索を介して見つけます。

take = 要求されるホモモルフィズムの数（この数に達した場合は検索プロセスを早期に停止します） max = この数のホモモルフィズムを超えた場合はエラーをスローします（例えば、0または1のホモモルフィズムを期待する場合はmax=1を設定します） filter = 一部の基準を満たすホモモルフィズムのみを考慮します。これは、ACSetTransformation -> Bool型のJulia関数として表現されます。

`take`と`max`の両方を指定することは意味がありません。
