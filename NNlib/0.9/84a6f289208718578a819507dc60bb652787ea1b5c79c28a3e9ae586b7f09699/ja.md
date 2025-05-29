```
istft(y;
    n_fft::Int, hop_length::Int = n_fft ÷ 4, window = nothing,
    center::Bool = true, normalized::Bool = false,
    return_complex::Bool = false,
    original_length::Union{Nothing, Int} = nothing,
)
```

逆短時間フーリエ変換。

元の信号の最小二乗推定を返します。

# 引数:

  * `y`: `(n_fft, n_frames, B)` 形状の入力複素配列。ここで `B` はオプションのバッチ次元です。

# キーワード引数:

  * `n_fft::Int`: フーリエ変換のサイズ。
  * `hop_length::Int`: 隣接するスライディングウィンドウフレーム間の距離。
  * `window`: `stft` の入力に適用されたウィンドウ関数。`nothing`（デフォルト）の場合、ウィンドウは適用されていません。
  * `center::Bool`: `stft` の入力が両側にパディングされていたかどうか。$t$-th フレームが時間 $t \times \text{hop length}$ で中心に配置されるようにします。パディングは `pad_reflect` 関数で行われます。
  * `normalized::Bool`: `stft` の入力が正規化されていたかどうか。
  * `return_complex::Bool`: 出力が複素数であるべきか、または入力が実信号とウィンドウから派生していると仮定すべきか。
  * `original_length::Union{Nothing, Int}`: `stft` の入力の最初の次元のオプションサイズ。正確な `stft` 入力サイズを復元するのに役立ちます。そうでない場合、配列は少し短くなる可能性があります。
