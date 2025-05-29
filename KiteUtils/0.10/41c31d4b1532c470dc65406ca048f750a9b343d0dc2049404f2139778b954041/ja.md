```
save_log(logger::Logger, name="sim_log", compress=true;
            path="",
            colmeta = Dict(:var_01 => ["name" => "var_01"],
                           :var_02 => ["name" => "var_02"],
                           :var_03 => ["name" => "var_03"],
                           :var_04 => ["name" => "var_04"],
                           :var_05 => ["name" => "var_05"],
                           :var_06 => ["name" => "var_06"],
                           :var_07 => ["name" => "var_07"],
                           :var_08 => ["name" => "var_08"],
                           :var_09 => ["name" => "var_09"],
                           :var_10 => ["name" => "var_10"],
                           :var_11 => ["name" => "var_11"],
                           :var_12 => ["name" => "var_12"],
                           :var_13 => ["name" => "var_13"],
                           :var_14 => ["name" => "var_14"],
                           :var_15 => ["name" => "var_15"],
                           :var_16 => ["name" => "var_16"]
        ))
```

ロガーからフライトログを .arrow ファイルとして保存します。デフォルトでは lz4 圧縮が使用されます。2 番目のパラメータに **false** を使用すると、圧縮は使用されません。
