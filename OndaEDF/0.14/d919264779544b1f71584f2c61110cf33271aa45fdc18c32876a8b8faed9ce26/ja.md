```
store_edf_as_onda(edf::EDF.File, onda_dir, recording_uuid::UUID=uuid4();
                  custom_extractors=STANDARD_EXTRACTORS, import_annotations::Bool=true,
                  signals_prefix="edf", annotations_prefix=signals_prefix)
```

`EDF.File`を`Onda.Samples`および`Onda.Annotation`に変換し、サンプルを`$path/samples/`に保存し、Ondaの信号および注釈テーブルを`$path/$(signals_prefix).onda.signals.arrow`および`$path/$(annotations_prefix).onda.annotations.arrow`に書き込みます。デフォルトのプレフィックスは「edf」であり、信号のプレフィックスが提供されているが注釈のプレフィックスが提供されていない場合、両方とも信号のプレフィックスを使用します。プレフィックスは（サブ）ディレクトリを参照できません。

`(; recording_uuid, signals, annotations, signals_path, annotations_path, plan)`を返します。

これは便利な関数であり、最初に[`plan_edf_to_onda_samples`](@ref)を介してインポートプランを策定し、その後すぐに[`edf_to_onda_samples`](@ref)を使用してこのプランを実行します。

サンプルと実行されたプランが返されます。未抽出の信号（`:sensor_type`または`:channel`が`missing`である場合）やエラー（`:error`に非`nothing`の値がある場合）についてプランを確認することを**強く推奨**します。

`EDF.Signal`のグループは、[`plan_edf_to_onda_samples`](@ref)を介して`Onda.Samples`のチャネルにマッピングされます。この関数の呼び出し元は、`labels`および`units`キーワード引数を介してプランを制御でき、これらはすべて[`plan_edf_to_onda_samples`](@ref)に転送されます。

Ondaチャネル名に変換される`EDF.Signal`ラベルは、以下の変換を受けます：

  * ラベルはホワイトスペースが削除され、括弧が削除され、小文字に変換されます
  * 末尾の一般的なEDF参照（例：「ref」、「ref2」など）は削除されます
  * `+`のインスタンスは`_plus_`に、`/`は`_over_`に置き換えられます
  * すべてのコンポーネント名は可能な限り「標準名」に変換されます（例：ECGに一致するチャネル名の「3」は「iii」に変換されます）。

より多くの制御（例：信号ラベルの前処理）が必要な場合、呼び出し元は[`plan_edf_to_onda_samples`](@ref)および[`edf_to_onda_samples`](@ref)を直接使用し、結果のサンプルを手動で`Onda.store`する必要があります。

EDFフォーマットの期待に関する追加の詳細については、OndaEDFのREADMEを参照してください。
