```
@APCdef(unitsystem = ACCELERATOR, unittype = Float, name = :APC)
```

## 説明:

物理定数と種の質量および電荷のゲッタ関数を適切な単位とデータで定義します。

## キーワードパラメータ:

  * `unitsystem`   – 型: `Unitful` 単位の5タプル。単位系を指定します。デフォルトは `ACCELERATOR` で、単位を「デフォルト単位」に設定します（下記参照）。他のオプションは `MKS` と `CGS` です。すべての単位を設定する便利な方法を提供します。
  * `unittype`     – 定数およびゲッタ関数の戻り値の型を設定します。`Float`、`Unitful`、または `DynamicQuantities` にできます。デフォルトは `Float` です。
  * `name`         – 定数およびゲッタ関数を含むモジュールの名前を設定します。デフォルトは `APC` です。

## 注意

  * @APCdef はモジュール内で一度だけ呼び出すことができます。

## デフォルト単位:

  * `mass`: eV/c^2
  * `length`: m
  * `time`: s
  * `energy`: eV
  * `charge`: 基本電荷
