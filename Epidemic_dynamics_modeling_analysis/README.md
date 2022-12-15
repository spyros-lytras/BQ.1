# Epidemic dynamics modeling analysis

## Summary
Motivated by the model established by Obermeyer et al, we developed a method to model the relationship between viral epidemic dynamics and S substitutions. This model can simultaneously estimate i) the effect of each S substitution on Re and ii) the relative Re of a viral group represented by each S haplotype. The key concept of the model used in this study is the same as the one in Obermeyer et al. However, our method is independent of the predefined viral classification such as PANGO lineage but based on the viral classification according to the profile of S substitutions. Therefore, our method can link the effect of S substitutions to viral epidemic dynamics in a more direct manner. Also, in our method, a Markov Chain Monte Carlo (MCMC) method is used for parameter estimation instead of variational inference, an approximation method.

We constructed a Bayesian hierarchal model, which represents the epidemic dynamics of each S haplotype according to growth rate parameters for each S haplotype, which is represented by a linear combination of the effect of S substitutions. Arrays in the model index over one or more indices: L = 254 viral lineages (i.e., S haplotypes) l; S = 107 substitutions/substitution clusters s; and T = 229 days t. The model is:

$$ \sigma_1\sim Student\_t^+\left(5,0,10\right) $$
$$$$
$$$$
$$$$
$$$$


The count of viral lineage l at time t, y_{lt}, is modeled as a hierarchal Multinomial logistic regression with intercept \alpha_l and slope \beta_l parameters for lineage l. The slope (or viral lineage growth) parameter \beta_l is generated from Student’s t distribution with five degrees of freedom, the mean value represented by f_mX_{lm}, and standard deviation, \sigma_1. f_mX_{lm} denotes the linear combination of the effect of each substitution, where f_m and X_{lm} are the effect of substitution m and the profile of substitution m in lineage l (i.e., the substitution profile matrix constructed in the above paragraph), respectively. As a prior of f_m, the Laplace distribution with the mean 0 and the standard deviation 10 was set. In other words, we estimated the parameter f_m in the framework of Bayesian least absolute shrinkage and selection operator (LASSO). As a prior of \sigma_1, a half Student’s t distribution with the mean 0 and the standard deviation 10 was set. For the other parameters, non-informative priors were set.
The relative Re of each viral lineage, r_l, was calculated according to the slope parameter \beta_l as:





