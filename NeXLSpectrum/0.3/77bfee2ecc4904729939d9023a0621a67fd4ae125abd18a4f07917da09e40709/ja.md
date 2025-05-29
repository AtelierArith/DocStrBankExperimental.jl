```
modelBackground(spec::Spectrum, chs::AbstractUnitRange{<:Integer}, ash::AtomicSubShell)
```

spec: chsの中心にピークを含むスペクトル chs: ピークを含むチャンネルの範囲 ash: エッジ（AtomicSubShellとして）

特性X線ピークの下の背景をモデル化するためのシンプルなモデルです。このモデルは、first(chs)およびlast(chs)の周りの低エネルギーおよび高エネルギーの背景領域に線をフィットさせます。低エネルギーの線がエッジエネルギーまで延びたとき、そのエネルギーで高エネルギーの線よりも大きい場合、2つの間に負のエッジがフィットされます。そうでない場合は、低エネルギー側と高エネルギー側の間に線がフィットされます。このモデルは、chsの範囲内にピーク干渉がないときにのみ機能します。

```
modelBackground(spec::Spectrum, chs::AbstractUnitRange{<:Integer})
modelBackground(spec::Spectrum, chs::AbstractUnitRange{<:Integer}, ash::AtomicSubShell)
```

`spec`: chsの中心にピークを含むスペクトル `chs`: ピークを含むチャンネルの範囲 `ash`: 特性ピークに関連するチャンネルの範囲内の最大エッジ

特性X線ピークの下の背景をモデル化するためのシンプルなモデルです。このモデルは、first(chs)およびlast(chs)の周りの低エネルギーおよび高エネルギーの背景領域の間に線をフィットさせます。このモデルは、chsの範囲内にピーク干渉がないときにのみ機能します。
