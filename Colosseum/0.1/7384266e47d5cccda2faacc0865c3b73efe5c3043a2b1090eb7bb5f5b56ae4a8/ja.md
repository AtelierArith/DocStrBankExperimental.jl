指定されたメッセージをシミュレーターのウィンドウに表示します。

message*paramが指定されている場合、それはメッセージの横に表示され、その場合、このAPIが同じメッセージ値で異なるmessage*paramを使用して呼び出されると、前の行が新しい行で上書きされます（APIが表示に新しい行を作成するのではなく）。

例えば、`simPrintLogMessage("Iteration: ", to_string(i))`は、異なるiの値でAPIが呼び出されると、表示上の同じ行を更新し続けます。severityパラメータの有効な値は0から3までで、異なる色に対応しています。

Args:     message (str) 表示するメッセージ     message_param (str, optional) メッセージの横に表示するパラメータ     severity (int, optional) メッセージの重大度に対応する範囲0-3（含む）
