`RelationalContainer`内の値は、名前またはシンボルによってアクセスされます。どちらの場合も、名前/シンボルは特定の名前空間に属します。シンボルでアクセスされると、親子関係はキーおよび非キーのデータ名の両方に対して認識されます。たとえば、カテゴリ`atom_site_aniso`が`atom_site`の子カテゴリである場合、`atom_site_aniso`のメンバー`u11`は、`:atom_site_aniso, :u_11`、`:atom_site, :u_11`、および`"_atom_site_aniso.u_11"`としてアクセスできます。

同様に、両方のカテゴリのキー データ名が`<cat name>.label`である場合、いずれかのカテゴリの特定の行は、次の4つの形式のいずれかを使用して示すことができます: `:atom_site, :label`、`:atom_site_aniso, :label`、`"*atom*site.label"`、または`"*atom*site_aniso.label"`。この後者の動作は、キー データ名の同等性から生じます。
