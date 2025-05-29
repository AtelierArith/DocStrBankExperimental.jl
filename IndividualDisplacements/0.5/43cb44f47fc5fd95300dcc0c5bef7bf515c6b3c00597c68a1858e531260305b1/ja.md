```
struct Individuals{T,N}
```

  * データ:           📌 (位置),   🔴(記録), 🆔 (ID), P (`FlowFields`)
  * 関数:           🚄 (速度),   ∫ (積分), 🔧(後処理)
  * NamedTuples:    D (診断),      M (メタデータ)

速度関数 🚄 は通常、指定された時空間領域内の個々の位置 (📌 から始まる) での速度を、グリッド化された変数 (P を介して提供される) を補間することによって計算します。個々の軌道は、時間を通じて補間された速度を積分 (∫) することによって計算されます。通常、積分は ∫! を呼び出すことによって行われ、最後に 📌 を更新し、🔴 に結果を 🔧 を介して記録します。例えば、🔧 で使用するための補助データは D に提供でき、メタデータは M に保存されます。

Unicode チートシート:

  * 📌=`\:pushpin:<tab>`,          🔴=`\:red_circle:<tab>`, 🆔=`\:id:<tab>`
  * 🚄=`\:bullettrain_side:<tab>`, ∫=`\int<tab>`,          🔧=`\:wrench:<tab>`
  * P=`\itP<tab>`,                 D=`\itD<tab>`,           M=`\itM<tab>`

`FlowFields` を使用して適切なデフォルトを選択するシンプルなコンストラクタ:

  * Individuals(F::uvArrays,x,y)
  * Individuals(F::uvwArrays,x,y,z)
  * Individuals(F::uvMeshArrays,x,y,fid)
  * Individuals(F::uvwMeshArrays,x,y,z,fid)

さらなるカスタマイズはキーワードコンストラクタを介して実現できます:

```
df=DataFrame( ID=[], x=[], y=[], z=[], t = [])
I=Individuals{Float64,2}(📌=zeros(3,10),🆔=1:10,🔴=deepcopy(df))
I=Individuals(📌=zeros(3,2),🆔=collect(1:2),🔴=deepcopy(df))
```

または、プレーンテキスト (またはノーUnicode) コンストラクタを介して:

```
df=DataFrame( ID=[], x=[], y=[], z=[], t = [])
I=(position=zeros(3,2),ID=1:2,record=deepcopy(df))
I=Individuals(I)
```
