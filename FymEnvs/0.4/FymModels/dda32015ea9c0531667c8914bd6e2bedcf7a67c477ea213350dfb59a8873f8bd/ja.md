module FymModels

このモジュールは、有名な飛行システムの環境とシステム、すなわち FymEnv と FymSystem を提供します。

[Usage]

  * FymEnv
  * FymSystem

f16 = F16LinearLateral(initial_state=ones(7)) systems = Dict("f16" => system(f16))

# 注意: typeof(system(fds::FymSystem)) == BaseSystem

function step(env)     update!(env)     next*obs = sys.state     done = time*over(env.clock)     return next*obs, zeros(1), done, Dict() end function set*dyn(env, t; deriv=deriv(f16))     sys = env.systems["f16"]     x = sys.state     u = zeros(2)     sys.dot = deriv(x, u) end

env = BaseEnv() systems!(env, systems) dyn!(env, set_dyn) step!(env, step) reset!(env)

⋮
