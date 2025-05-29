```
sc_hash_function_string(s, u)
```

ヌル終端文字列からハッシュ値を計算します。このハッシュ関数は暗号的に安全ではありません！その場合はlibcryptを使用してください。

### パラメータ

  * `s`:[in] ハッシュ化されるヌル終端文字列。
  * `u`:[in] 使用されません。

### 戻り値

計算されたハッシュ値を符号なし整数として返します。

### プロトタイプ

```c
unsigned int sc_hash_function_string (const void *s, const void *u);
```
