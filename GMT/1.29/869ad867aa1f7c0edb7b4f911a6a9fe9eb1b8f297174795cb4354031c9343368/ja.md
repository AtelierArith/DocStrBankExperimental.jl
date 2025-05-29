```
Igray = rgb2gray(I::GMTimage{UInt8, 3}) -> GMTimage{UInt8, 2}
```

RGB画像をテレビYMQ変換を適用してグレースケール画像に変換します。

### 引数

  * `I::GMTimage{UInt8, 3}`: UInt8型の入力画像。

### 戻り値

新しい$GMTimage{UInt8, 2}$。

### 例

```jldoctest
I = gmtread(GMT.TESTSDIR * "assets/bunny_cenora.jpg");
Igray = rgb2gray(I)

# 2つを横に並べて表示
grdimage(I, figsize=6)
grdimage!(Igray, figsize=6, xshift=6.1, show=true)
```
