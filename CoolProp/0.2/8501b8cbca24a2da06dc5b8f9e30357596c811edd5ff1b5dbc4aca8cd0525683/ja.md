```
AbstractState_build_phase_envelope(handle::Clong, level::AbstractString)
```

位相エンベロープを構築します。

# 引数

  * `handle`: メモリに保存された状態クラスの整数ハンドル
  * `level`: 位相エンベロープの精緻化の程度 ("none" は精緻化をスキップする (推奨) または "veryfine")

# 注意

入力のいずれかの更新呼び出しにエラーがある場合、出力配列には変更が加えられません。

# 参照

CoolPRop::AbstractState*build*phase*envelope(const long handle, const char* level, long* errcode, char* message*buffer, const long buffer_length);
