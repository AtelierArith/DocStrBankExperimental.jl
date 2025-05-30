filter*array*nospace(array,smooth_t,position=1)

入力の1次元配列をフィルタリングします。境界値は複製されますが、position = 2の場合は、平滑化された配列の内側の部分のみを取得します。

この関数は、Images.jlのimfilter関数を内部で呼び出します。
