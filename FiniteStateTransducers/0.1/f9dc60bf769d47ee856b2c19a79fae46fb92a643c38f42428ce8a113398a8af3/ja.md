`topsortperm(fst::WFST, i = get_initial(fst); filter=arc->true)`

`fst`が非循環である必要があります。

`i`-番目の状態から始まる`fst`の状態のトポロジカル順序を返します。

`filter`関数を修正して、特定のアークのみを考慮して操作を実行します。
