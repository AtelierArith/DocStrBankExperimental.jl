```
rect(cornerpoint, w, h; action = none, reversepath=false,
    vertices=false)
rect(cornerpoint, w, h, action; reversepath=false,
    vertices=false)
```

`cornerpoint`で1つの隅を持ち、幅`w`と高さ`h`の長方形を作成し、現在のパスに追加します。そして`action`を適用します。

`vertices=true`を使用すると、4つの隅のポイントの配列が返されます：左下、左上、右上、右下。

`reversepath`はパスの方向を逆にし（ポイントを左下、右下、右上、左上の順で返します）。

4つの隅の頂点を返します。
