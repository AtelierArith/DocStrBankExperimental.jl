imgnormalize - 画像の値を0-1に正規化する、または希望する平均と分散に正規化する

```
Usage 1:      nimg = imgnormalize(img)
```

画像をオフセットし、再スケールして最小値を0、最大値を1にします。

```
Usage 2:      nimg = imgnormalize(img, reqmean, reqvar)

Arguments:  img     - グレースケールの入力画像。
            reqmean - 画像の必要な平均値。
            reqvar  - 画像の必要な分散。
```

画像をオフセットし、再スケールしてnimgが平均reqmeanおよび分散reqvarを持つようにします。
