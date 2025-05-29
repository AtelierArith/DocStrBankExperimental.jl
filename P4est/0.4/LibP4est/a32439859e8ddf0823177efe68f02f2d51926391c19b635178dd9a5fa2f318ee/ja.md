```
sc_io_sink_destroy(sink)
```

データシンクを解放します。[`sc_io_sink_complete`](@ref)を呼び出し、最終的なカウントを破棄します。completeからのエラーは、この関数からSC*IO*ERROR*FATALが返されます。bytes*outが重要な場合は、自分で[`sc_io_sink_complete`](@ref)を呼び出してください。

### パラメータ

  * `sink`:[in,out] 完了して解放するシンクオブジェクト。

### 戻り値

成功時は0、エラー時は非ゼロ。

### プロトタイプ

```c
int sc_io_sink_destroy (sc_io_sink_t * sink);
```
