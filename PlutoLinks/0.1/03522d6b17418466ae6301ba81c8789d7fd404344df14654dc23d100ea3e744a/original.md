The `@revise` macro imports a package watched by Revise. The cell from which `@revise` is called will be re-run whenever the package definition changes. This means that cells depending on this package will be updated as well.

  * The revised package should be developed in the current environment, usually requiring you to [opt out of the Pluto package manager](https://github.com/fonsp/Pluto.jl/wiki/%F0%9F%8E%81-Package-management#advanced-set-up-an-environment-with-pkgactivate).

---

Examples

```julia
# in one cell
using PlutoLinks

# in another cell
@revise using MyPackage

# import is also supported
@revise import MyPackage
```
