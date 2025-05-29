An improvement of the COEVOLVE algorithm for simulating any compound jump process that evolves through time. This method handles variable intensity rates with user-defined bounds and inter-dependent processes. It reduces to NRM when rates are constant. As opposed to COEVOLVE, this method syncs the thinning procedure with the stepper which allows it to handle dependencies on continuous dynamics.

G. A. Zagatti, S. A. Isaacson, C. Rackauckas, V. Ilin, S.-K. Ng and S. Bressan, Extending JumpProcess.jl for fast point process simulation with time-varying intensities, arXiv. doi:10.48550/arXiv.2306.06992.

M. Farajtabar, Y. Wang, M. Gomez-Rodriguez, S. Li, H. Zha, and L. Song, COEVOLVE: a joint point process model for information diffusion and network evolution, Journal of Machine Learning Research 18(1), 1305–1353 (2017). doi: 10.5555/3122009.3122050.
