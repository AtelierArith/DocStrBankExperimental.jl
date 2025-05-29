For a prob::ODEProblem, with nominal parameters p0, creates a cost function C(p)  Let pprob = remake(prob, p=p). C(p) is the collocation cost associated with  pprob. Calculated by integrating the following over the trajectory of solve(prob; saveat=tsteps):

int_u  sum(pprob.f(u) - prob.f(u)).^2

with output map g(x), this turns into 

int_u  sum(dgdx(u)*pprob.f(u) - dgdx(u)*prob.f(u)).^2
