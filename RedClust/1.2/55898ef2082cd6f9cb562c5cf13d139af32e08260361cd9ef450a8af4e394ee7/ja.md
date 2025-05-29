summarise([io::IO], clusts::ClustLabelVector, truth::ClustLabelVector, printoutput = true) -> String `clusts`のクラスタリング精度の要約を、`truth`の真の値に対して印刷します。出力は、提供されていない場合はデフォルトで`stdout`となる出力ストリーム`io`に印刷されます。
