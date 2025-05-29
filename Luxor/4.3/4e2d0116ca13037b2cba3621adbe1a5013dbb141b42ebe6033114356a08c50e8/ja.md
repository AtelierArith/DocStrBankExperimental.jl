```
sethue("black")
sethue(0.3, 0.7, 0.9)
setcolor(sethue("red")..., .2)
```

不透明度を変更せずに色を設定します。

`sethue()`は`setcolor()`のようなもので、現在の色を不透明度を変更せずに変更したい場合があります。`setcolor()`の代わりに`sethue()`を使用すると、現在のアルファ不透明度は変更されません。

詳細は[`setcolor`](@ref)を参照してください。
