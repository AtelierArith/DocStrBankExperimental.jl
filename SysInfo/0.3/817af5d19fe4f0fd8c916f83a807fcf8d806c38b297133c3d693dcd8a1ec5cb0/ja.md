`i`番目のNUMAドメインに属するCPU IDを返します（論理インデックス、1から始まります）。デフォルトでは、「ハイパースレッドの前のコア」順序が使用されます。コンパクトな順序が必要な場合は、`compact=true`を設定してください。ランダム化するには、`shuffle=true`を設定します。

オプションの第2引数：CPUスレッドのサブセットを選択するための論理インデックス。
