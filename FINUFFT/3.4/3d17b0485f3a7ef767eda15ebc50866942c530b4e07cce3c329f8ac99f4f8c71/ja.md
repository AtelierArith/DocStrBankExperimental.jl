```
mutable struct nufft_opts
    modeord            :: Cint
    spreadinterponly   :: Cint
    debug              :: Cint
    spread_debug       :: Cint
    showwarn           :: Cint
    nthreads           :: Cint
    fftw               :: Cint
    spread_sort        :: Cint
    spread_kerevalmeth :: Cint
    spread_kerpad      :: Cint
    upsampfac          :: Cdouble
    spread_thread      :: Cint
    maxbatchsize       :: Cint
    spread_nthr_atomic :: Cint
    spread_max_sp_size :: Cint
    fftw_lock_fun      :: Ptr{Cvoid}
    fftw_unlock_fun    :: Ptr{Cvoid}
    fftw_lock_data     :: Ptr{Cvoid}
end
```

FINUFFTライブラリに渡されるオプション構造体。

# フィールド

これは概要のみです。完全な説明についてはFINUFFTのドキュメントを参照してください。

```
modeord :: Cint
```

0: CMCLスタイルの増加モード順序（負から正）、または 1: FFTスタイルのモード順序（タイプ1,2のみに影響）

```
spreadinterponly :: Cint
```

（タイプ1,2のみ）  0: 実際のNUFFTを実行  1: スプレッドのみ（タイプ1の場合）または補間（タイプ2）       debug :: Cint 0 サイレント、1 一部のタイミング/デバッグ、または2 さらに多く

```
spread_debug :: Cint
```

スプレッダー: 0 サイレント、1 一部のタイミング/デバッグ、または2 トン

```
showwarn :: Cint
```

0 警告をstderrに印刷しない、1 印刷する

```
nthreads :: Cint
```

使用するスレッドの数、または0はすべての利用可能なスレッドを使用

```
fftw :: Cint
```

FFTWへのプランフラグ（FFTW*ESTIMATE=64、FFTW*MEASURE=0、...）

```
spread_sort :: Cint
```

スプレッダー: 0 ソートしない、1 ソートする、または2 ヒューリスティック選択

```
spread_kerevalmeth :: Cint
```

スプレッダー: 0 exp(sqrt())、1 ホーナーの区分多項式（より速い）

```
spread_kerpad :: Cint
```

（exp(sqrt())のみ）: 0 カーネルを4nにパディングしない、1 する

```
upsampfac :: Cdouble
```

アップサンプリング比σ: 2.0 標準、1.25 小さなFFT、0.0 自動

```
spread_thread :: Cint
```

（ベクトル化されたntr>1のみ） 0: 自動 1: 逐次マルチスレッド 2: 並列シングルスレッドスプレッド

```
maxbatchsize :: Cint
```

（ベクトル化されたntr>1のみ）: 最大変換バッチ、0 自動

```
spread_nthr_atomic :: Cint
```

> =0の場合、スプレッダーのOMPクリティカルがアトミックになるスレッド数


```
spread_max_sp_size :: Cint
```

> 0の場合、スプレッダー（dir=1）の最大サブ問題サイズをオーバーライド


```
fftw_lock_fun      :: Ptr{Cvoid}
```

FFTWプランナーをロックする関数ポインタ  Cシグネチャ: `void (*fftw_lock_fun)(void *)`

```
fftw_unlock_fun    :: Ptr{Cvoid}
```

FFTWプランナーのロックを解除する関数ポインタ  Cシグネチャ: `void (*fftw_unlock_fun)(void *)`

```
fftw_lock_data     :: Ptr{Cvoid}
```

ロック関数に渡すデータ（例: ミューテックス）  Cシグネチャ: `void *fftw_lock_data`
