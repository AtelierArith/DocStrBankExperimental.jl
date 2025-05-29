このマクロは、evalブロックに関連付けられた`/output/`フォルダーを指します。したがって、たとえば、evalブロックがプロットを生成する場合、`savefig(joinpath(@OUTPUT, "ex1.png"))`のようにしてプロットを保存できます。
