# The Analysis
## 1. What are the most demanded skills for the top 3 most popular data roles? 

To find the most demanded skills for the top 3 most popular data roles, I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the role I'm targetting.

View my notebook with detailed steps here:  
[2.Skill_Demand_ipynb](Final%20Project/2_Skill_Demand.ipynb)

### Visualize Data 

```python
fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)

    sns.barplot(
        data=df_plot,
        x='skill_percentage',
        y='job_skills',
        ax=ax[i],
        palette='dark:b_r'
    )

    ax[i].set_title(job_title)
    ax[i].set_xlim(0, 70)

    for n, v in enumerate(df_plot['skill_percentage']):
        ax[i].text(v + 1, n, f'{round(v)}%', va='center')

fig.suptitle('Likelihood of Skills Requested in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=0.5)
plt.show()
```

### Results

![Visualizations of Top Skills](Final%20Project\images\Skill_demand_all_data_roles.png)

### Insights    

- Python serves as the ultimate bridge skill, ranking as the top priority for Software Engineers (55%) while maintaining a strong footprint for Data Analysts (35%).
- SEO (68%) is the single most dominant skill across any role, though Marketing Managers are concurrently expected to have high proficiency across data analytics, email, and social media.
- For Data Analysts, traditional data retrieval and management tools like SQL (52%) and Excel (46%) remain more heavily requested than Python or standalone visualization software.