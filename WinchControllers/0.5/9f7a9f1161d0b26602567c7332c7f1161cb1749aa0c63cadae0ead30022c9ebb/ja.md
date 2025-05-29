```
select_b(m3::Mixer_3CH, select_b::Bool)
```

入力 b をアクティブ入力にします。

チャンネル a をアクティブ入力にするには、次のように呼び出します：

```julia
select_b(m3, false)
select_c(m3, false)
```

### パラメータ

  * m3::Mixer_3CH: 三チャンネルミキサー
  * select_b: true の場合、チャンネル b を選択

### 戻り値

  * 何も返さない
