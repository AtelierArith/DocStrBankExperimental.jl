These are helpers for weighting integrals of p.d.f.s for calculating basic stats.

The main idea of doing it this way is to have a single instance of these to reuse specializations and to use structs so as to be able to control the level of specialization.
