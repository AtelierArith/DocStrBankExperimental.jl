imgnormalise/imgnormalize - 画像の値を0-1に正規化するか、希望する平均と分散に正規化します。

```
Usage 1:      nimg = imgnormalise(img)
```

画像をオフセットし、再スケールして最小値を0、最大値を1にします。

```
Usage 2:      nimg = imgnormalise(img, reqmean, reqvar)

Arguments:  img     - グレースケールの入力画像。
            reqmean - 画像の希望する平均値。
            reqvar  - 画像の希望する分散。
```

画像をオフセットし、再スケールしてnimgが平均reqmeanおよび分散reqvarを持つようにします。
