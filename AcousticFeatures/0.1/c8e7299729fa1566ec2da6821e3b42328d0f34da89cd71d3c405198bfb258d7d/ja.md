パワースペクトルを計算するための演算子

# コンストラクタ

```
PowerSpec(;
          fs       :: Int = 16000,          # サンプリング周波数
          fmin     :: Real = 0,             # 最小周波数
          fmax     :: Real = fs/2,          # 最大周波数
          winlen   :: Int = 256,            # ウィンドウ長
          dilation :: Int = 1,              # ダウンサンプル比
          stride   :: Int = winlen/2,       # 隣接フレーム間の距離
          nffts    :: Int = winlen,         # FFT変換のビン
          donorm   :: Bool = false,         # スペクトルを正規化するかどうか
          winfunc  :: Function = hanning,   # ウィンドウ関数
          type     :: DataType = Vector{Float32})
```

ここで、[`fmin`, `fmax`]は関心のある周波数領域であり、`type`は入力の型（行列またはベクトル）です。`donorm`がtrueの場合、ウィンドウの要素はウィンドウエネルギーの平方根で割られます。
