```
smooth_vars_and_write_to_netcdf!(output_file,input_file,vars_to_smooth,window_h,window_t)
```

NetCDFファイル、変数のリスト、2つの整数を受け取り、これらの変数の移動平均スムージングを実行します。スムージングされたフィールドをoutput_fileという名前のNetCDFファイルに書き込みます。
