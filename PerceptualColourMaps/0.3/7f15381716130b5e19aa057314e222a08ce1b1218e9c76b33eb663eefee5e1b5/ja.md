normalise/normalize - 画像の値を0-1に正規化するか、希望する平均と分散に正規化します。

```
Usage 1:      nimg = normalise(img)
```

画像をオフセットし、最小値を0、最大値を1にスケーリングします。

```
Usage 2:      nimg = normalise(img, reqmean, reqvar)

Arguments:  img     - グレーレベルの入力画像。
            reqmean - 画像の必要な平均値。
            reqvar  - 画像の必要な分散。
```

画像をオフセットし、nimgが平均reqmeanおよび分散reqvarを持つようにスケーリングします。
