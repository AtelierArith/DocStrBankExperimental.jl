GMT manipulating geographic and Cartesian data sets (including filtering, trend fitting, gridding, projecting, etc.) and producing high quality illustrations.

Documentation for GMT.jl at https://www.generic-mapping-tools.org/GMTjl_doc

---

The GMT.jl default is to use the GMT_jll artifact. However, this can be changed to use a system wide GMT installation. All info is stored in the `deps/deps.jl` file that is created by compile from the `deps/build.jl`. To swap to a system wide GMT installation, do (in REPL):

  * ENV["SYSTEMWIDE_GMT"] = 1;
  * import Pkg; Pkg.build("GMT")
  * restart Julia

Note the above will work up until some other reason triggers a Julia recompile, where the JLL artifacts  will be used again. To make the ENV["SYSTEMWIDE*GMT"] = 1 solution permanent, declare a "SYSTEMWIDE*GMT" environment variable permanently in your .bashrc (or whatever).
