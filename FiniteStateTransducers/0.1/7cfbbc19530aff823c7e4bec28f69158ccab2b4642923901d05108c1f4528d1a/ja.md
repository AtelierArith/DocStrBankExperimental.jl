`topsort(fst::WFST, i = get_initial(fst); filter=arc->true)`

`fst`は非循環である必要があります。

`i`-番目の状態から始まるトポロジカルソートされた`fst`と同等のWFSTを返します。

`filter`関数を修正して、特定のアークのみを考慮して操作を実行します。
