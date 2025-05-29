run_mh(data,model,options)

returns fits, stats, measures

Run Metropolis-Hastings MCMC algorithm and compute statistics of results

-`data`: AbstractExperimentalData structure -`model`: AbstractGeneTransitionModel structure with a logprior function -`options`: MHOptions structure

model and data must have a likelihoodfn function
