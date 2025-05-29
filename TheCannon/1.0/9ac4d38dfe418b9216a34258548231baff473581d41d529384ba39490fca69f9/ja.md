ラベルを標準化されていない形式に戻します。返すのは

labels.*transpose(hcat(scale)) .+ transpose(hcat(pivot))
