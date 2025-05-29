デフォルトで[`output_csv()`](@ref)によって出力されるpar配列の数量のインデックス。キーがpar配列の名前で、値がインデックスの配列であるDict()としてフォーマットされています。この選択はpar配列の最初の次元に沿ったものであることに注意してください（すなわち、数量を選択するものであり、ミッションやフライトポイントを選択するものではありません）。

カスタムDicts()は、次のフォーマットに従って[`output_csv()`](@ref)に渡すことができます: `Dict(){String => Union{AbstractVector,Colon(), Integer}}`。

例えば: 1 : `default_output_indices["parg"] = [1, 5, igtotal]`         > `output_csv()`に送信されると、`parg`の最初、5番目、最後のエントリを列として出力します。

2 : `default_output_indices["para"] = Colon() #NOT [Colon()]`         > `output_csv()`に送信されると、`para`のすべてのインデックスを出力します（すべてのフライトまたはミッションが含まれるかどうかは別のパラメータによって制御されます）。
