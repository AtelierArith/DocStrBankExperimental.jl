```
get_video_data!(id::Integer, buffer, timeout_ms)
```

指定されたバッファにビデオフレームを書き込みます。バッファがフレームを収容できる十分な大きさであることを確認してください。ループ内でできるだけ早くこれを呼び出し、戻り値が ASI_SUCCESS と等しいかどうかを確認してください。

# 引数:

```
id: カメラID
buffer: ビデオフレームを書き込むためのバッファ。
timeout_ms: フレームを待つ時間。推奨: 2 * exposure_μs + 500 ms <- 一貫性のない単位？！
```

# 戻り値:

```
ASI_ERROR_CODE、これは ASI_SUCCESS であるべきです。
```
