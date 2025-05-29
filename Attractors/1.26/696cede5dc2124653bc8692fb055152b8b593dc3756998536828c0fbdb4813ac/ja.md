```
matching_map(
    a₊::Dict, a₋::Dict, matcher;
    ds::DynamicalSystem, p, pprev, next_id
) → rmap
```

IDを値にマッピングする辞書`a₊, a₋`が与えられたとき、*置換マップ*を返します：辞書`a₊`のID（キー）を辞書`a₋`のID（キー）にマッピングする辞書で、`a₋`の値に「最も近い」`a₊`の値が`a₋`と同じキーに割り当てられるようにします。このようにして、`a₊`のキーが`a₋`のキーに「マッチ」します。`swap_dict_keys`(@ref)を使用して、`rmap`を`a₊`または`a₊`と同じキーを持つ他の辞書に適用します。

マッチングがどのように行われるか、すなわち「近さ」がどのように定義されるかは、アルゴリズム`matcher`に依存します。

`a₊, a₋`に含まれる値は、`matcher`によってサポートされるものであれば何でもかまいません。Attractors.jl内では、通常、アトラクタを表す`StateSpaceSet`です。通常、+,-は動的システムのパラメータの変化の前後を意味します。

`matching_map`は、`a₊, a₋`のいずれかが空である場合、常に空の辞書を返します。

## キーワード引数

  * `ds`: `a₊, a₋`を生成した動的システム。
  * `p, pprev`: `a₊, a₋`に対応するパラメータ。両方ともパラメータインデックスをパラメータ値にマッピングする反復可能なものである必要があります（例えば`Dict, Vector{Pair}`など、`DynamicalSystems.set_parameters!`に入力できるものであれば何でも）。
  * `next_id = next_free_id(a₊, a₋)`: `a₊`の値が`a₋`にマッチできず、新しい一意のIDを取得する必要がある場合に与えるID。

`MatchBySSSetDistance`(@ref)のような一部のマッチャーは、`ds, p, pprev`を何らかの方法で利用しませんが、`MatchByBasinEnclosure`(@ref)のような他のマッチャーは利用し、これらは`ds, p, pprev`に値を明示的に与える必要があります。デフォルト値は単に`nothing`です。
