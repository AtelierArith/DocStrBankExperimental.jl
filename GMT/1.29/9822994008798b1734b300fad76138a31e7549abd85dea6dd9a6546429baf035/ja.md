```
J = imhmin(I::GMTimage{<:UInt8, 2}, H; conn=4)::GMTimage
```

H-最小値変換を使用して画像内の地域的最小値を抑制します。

H-最小値変換は、すべての地域的最小値の深さを最大で `H` まで減少させます。その結果、深さが `H` 未満の地域的最小値は完全に抑制されます。地域的最小値は、同じ強度値 t を持つ接続されたピクセルであり、強度値が t より大きいピクセルに囲まれています。

### 引数

  * `I::GMTimage{<:UInt8, 2}`: 入力画像。
  * `H`: バンプの最大地域深度。

### キーワード引数

  * `conn::Int=4`: I 内の地域的最大値を特定するために使用される接続性値（4 または 8）。デフォルトは 4 です。

### 戻り値

`I` と同じ型の新しい $GMTimage$。

### 例

```julia
a = fill(UInt8(10),10,10);
a[2:4,2:4] .= 7;  
a[6:8,6:8] .= 2;
a[1:3,7:9] .= 13;
a[2,8] .= 10;
I = imhmin(mat2img(a), 4);
```
