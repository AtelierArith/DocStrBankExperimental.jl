```julia
DataFunction(
    kernel::Function,
    argsizes;
    Tv,
    Ti,
    dependencies,
    bonus_quadorder,
    name
) -> GradientRobustMultiPhysics.DataFunction{Float64, Int32, _A, _B, _C, _D, _E, <:Function} where {_A, _B, _C, _D, _E}

```

は、PDEオペレーター、補間などの構築に使用できるDataFunctionを生成し、基本的にはユーザーによって指定されたカーネル関数と引数の次元および追加の依存関係に関する情報で構成されています：

  * kernel   : インターフェースを持つ関数 (result, ...)
  * argsizes : [result, interface] の期待される長さ

オプションの引数：

  * dependencies    : カーネルが空間座標 (X)、時間 (T)、アイテム (I)、ローカル座標 (L) にも依存するかどうかを指定する "XTIL" の部分文字列
  * bonus_quadorder : 組み立て中に使用されるFESpacesに基づいて計算された数値積分の次数に追加される
  * name            : 印刷メッセージで使用されるこのアクションの名前
  * Tv              : 結果/入力の期待されるNumberType
  * Ti              : グリッド列挙情報の期待されるNumberType (例： "I" 依存関係が使用される場合のアイテム/領域番号)
