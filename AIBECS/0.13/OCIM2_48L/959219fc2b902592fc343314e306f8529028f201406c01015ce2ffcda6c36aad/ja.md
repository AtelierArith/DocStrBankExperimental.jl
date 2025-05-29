この `OCIM2_48L` モジュールは、AIBECSで使用するためにOCIM2-48L行列とグリッドをロードするために使用されます。

!!! tip
    デフォルトのOCIM2_48L行列とグリッドをロードするには、次のようにします。

    ```
    julia> grd, T = OCIM2_48L.load()
    ```

    ただし、他の行列をロードするには、希望するバージョンを指定することもできます。例えば、

    ```
    julia> grd, T = OCIM2_48L.load(version="OCIM2_48L_KiHIGH_noHe")
    ```

    詳細については、*DeVries and Holzer* (2019)を参照してください。


!!! note
    FigShareのパブリックで永続的なURLからダウンロードされたファイルは、https://github.com/briochemc/OceanCirculations で入手可能なコードを使用して作成されました。

