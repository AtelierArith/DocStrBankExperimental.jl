normalize - 画像の値を0-1に正規化するか、所望の平均と分散に正規化します。

```
Usage 1:      nimg = normalize(img)
```

画像をオフセットし、再スケールして最小値を0、最大値を1にします。

```
Usage 2:      nimg = normalize(img, reqmean, reqvar)

Arguments:  img     - グレーレベルの入力画像。
            reqmean - 画像の所望の平均値。
            reqvar  - 画像の所望の分散。
```

画像をオフセットし、再スケールしてnimgが平均reqmeanおよび分散reqvarを持つようにします。
