# Project Cycle 3: Variable Notes & Assumptions

## 📝 Variable Coding & Recoding Details
1. **Grouping Variable (`WhatIsYourSex`)**:
   * Original Code: `1` represents Male, `2` represents Female.
   * This project directly utilizes these binary groups for two-sample comparisons, satisfying the structural prerequisite for inferential testing.

2. **Weight Response Variable (`HowMuchDoYouWeighWithoutShoesInKG`)**:
   * Attribute: Continuous / Quantitative Response.
   * Recoding Logic: The raw YRBS dataset contains numerous `99.99` entries. According to the official user guide, this represents a "Missing/Skip" code rather than actual weight. Treating it as numeric severely distorts the analysis (e.g., causing the female mean weight to falsely inflate to 74 kg). By filtering the data within a reasonable biological range of [30, 90) kg, we successfully restored the authentic population characteristics.

3. **Height Response Variable (`HowTallAreYouWithoutShoesInMeters`)**:
   * Attribute: Continuous / Quantitative Response.
   * Recoding Logic: Observations were filtered within [1.0, 2.2) meters to discard the official `9.99` missing codes and extreme invalid entries, securing the accuracy of our statistical inference.

## ⚠️ Assumption Awareness
This project strictly follows the default expectations by conducting a **Welch's Two-Sample t-test** (equal variances not assumed). The evaluation of the three core statistical assumptions is detailed below:
1. **Independence**: The data is obtained from the YRBS 2007 random sample survey. The two groups (Male vs. Female) and individual responses are mutually independent.
2. **Normality and Sample Size**: Although human weight and height distributions might exhibit slight skewness, our effective sample sizes for both groups are exceptionally large ($n > 6000$ for each). By the **Central Limit Theorem (CLT)**, the sampling distribution of the sample means will asymptotically approach a normal distribution. Therefore, Welch's t-test remains highly robust.
3. **Equal Variances**: We do not assume equal population variances between the two groups. Applying Welch's t-test protects the analysis from inflating Type I error rates, which aligns with rigorous academic standards.