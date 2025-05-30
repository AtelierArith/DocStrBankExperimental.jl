`EarthSciMLBase.Operator`を作成して、輸送を実行します。輸送は、指定された`stencil`オペレーター（例：`l94_stencil`または`ppm_stencil`）を使用して実行されます。`p`は、ステンシルオペレーターによって使用されるオプションのパラメーターです。`bc_type`は境界条件のタイプで、例として`ZeroGradBC()`があります。

風場データは、利用可能な場合に自動的に追加されます。現在、風データの有効なソースは`EarthSciData.GEOSFP`のみです。
