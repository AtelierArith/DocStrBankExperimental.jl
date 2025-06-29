```
種構造体:
```

Particle構造体は、選択した粒子に特有の情報を追跡するために使用されます。

## フィールド:

1. `name::String': 				粒子の名前
2. `int_charge::typeof(1u"q")': 				 粒子のネット電荷（|e|単位）

```
																	 	 - 帳簿管理のみ、したがって内部単位
																		 - 'charge()'関数を使用して、希望の単位で電荷を取得
```

3. `mass::typeof(1.0u"eV/c^2")': 				 粒子の質量（eV/c^2単位）

```
																		 - 帳簿管理のみ、したがって内部単位
																	 	 - 'mass()'関数を使用して、希望の単位で質量を取得
```

4. `spin::typeof(1.0u"h_bar")': 					 粒子のスピン（ħ単位）
5. `moment::typeof(1.0u"eV/T")': 					 粒子の磁気モーメント（eV/T単位）
6. `iso::Int': 												 粒子が原子同位体である場合、これは

```
																		 - 質量数、そうでなければ-1
```

7. `kind::Kind.T': 									 粒子の種類（ATOM, HADRON, LEPTON, PHOTON, NULL）                                     - NULL種類は実際の粒子ではないnull粒子を定義し                                      - プレースホルダーです

## コンストラクタ:

この構造体には次のコンストラクタがあります。

```
Species(speciesname::String)
```

このコンストラクタは、粒子の名前を指定することで、亜原子粒子または原子種の種構造体を作成するために使用されます。

このコンストラクタを使用する方法はいくつかあります。

1. 粒子が亜原子種を構成する場合、亜原子種の名前をフィールド名に入れます。

名前は正確に提供する必要があります。

2. 粒子が原子種である場合、同位体と電荷情報とともに原子記号を名前に入れます。

      * 原子種の名前は次の形式である必要があります：

    "質量数" + "原子記号" + "電荷" 質量数は原子記号の前に、電荷は最後に配置します。

      * 質量数と電荷はオプションです。
      * 質量数はUnicode上付き文字またはASCIIで、前にオプションの"#"を付けることができます。

    例:   Species("¹H") - 水素-1  Species("1H") - 水素-1  Species("#1H") - 水素-1

      * 質量数が指定されていない場合、最も豊富な同位体が使用されます。
      * 電荷は次の形式で指定できます：

          * "+"は単一の正電荷を表します
          * "++"は二重正電荷を表します
          * "+n"または"n+"はnの正電荷を表し、nはUnicode上付き文字にできます
          * "-"は単一の負電荷を表します
          * "–-"は二重負電荷を表します
          * "-n"または"n-"はnの負電荷を表し、nはUnicode上付き文字にできます

    例:   Species("C+") - 単一の正電荷を持つ炭素  Species("N³⁻") - 3の負電荷を持つ窒素

      * 電荷が指定されていない場合、電荷は0になります。
3. null種を作成するには、名前に"Null"または"null"または""を使用します。
4. 反粒子を作成するには、粒子の名前の前に"anti-"を付けます。 例: Species("anti-H") - 反水素 Species("anti-Fe") - 反鉄 Species("anti-positron") - 陽電子
