```
read_final_state_particles(fname; maxevents = -1, skipevents = 0, T=PseudoJet)
```

ファイルから最終状態の粒子を読み込み、それらを型Tのベクターとして返します。

# 引数

  * `fname`: 粒子を読み込むHepMC3 ASCIIファイルの名前。ファイルがgzippedの場合、関数は自動的に解凍します。
  * `maxevents=-1`: 読み込む最大イベント数。-1はすべてのイベントを読み込むことを意味します。
  * `skipevents=0`: イベントが含まれる前にスキップするイベントの数。
  * `T=PseudoJet`: 構築して返すオブジェクトの型。

# 戻り値

Tオブジェクトのベクターのベクターを返します。各内側のベクターは特定のイベントのすべての粒子を表します。特にTは`PseudoJet`または`LorentzVector`型であることができます。注意、Tが`PseudoJet`でない場合、コンストラクタの引数の順序は`(t, x, y, z)`でなければなりません。
