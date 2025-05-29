gaussfilt -  便利なガウスフィルタリングのための小さなラッパー関数

```
Usage:  smimg = gaussfilt(img, sigma)

Arguments:  img - スムージングされる画像、マルチチャネル可能。
                  ::Array{T,2}  または ::Array{T,3}
          sigma - ガウスフィルタの標準偏差。

Returns:  smimg - スムージングされた画像。
```

sigma = 0 で呼び出された場合、関数は即座に img を smimg に割り当てて返します。
