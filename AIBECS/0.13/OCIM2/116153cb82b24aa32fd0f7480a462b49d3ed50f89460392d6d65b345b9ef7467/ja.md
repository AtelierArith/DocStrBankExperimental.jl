この `OCIM2` モジュールは、AIBECSで使用するためにOCIM2行列とグリッドをロードするために使用されます。

!!! tip
    デフォルトのOCIM2行列とグリッドをロードするには、次のようにします。

    ```
    julia> grd, T = OCIM2.load()
    ```

    ただし、使用したいバージョンを指定することで他の行列をロードすることもできます。例えば、

    ```
    julia> grd, T = OCIM2.load(version="OCIM2_KiHIGH_noHe")
    ```

    詳細については *DeVries and Holzer* (2019) を参照してください。


!!! note
    FigShareの公共で永続的なURLからダウンロードされたファイルは、https://github.com/briochemc/OceanCirculations で入手可能なコードを使用して作成されました。

