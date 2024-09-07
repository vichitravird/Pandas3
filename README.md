# Pandas3

## 1 Problem 1 :Calculate Special Bonus ( https://leetcode.com/problems/calculate-special-bonus/)
<br>
import pandas as pd

def calculate_special_bonus(employees: pd.DataFrame) -> pd.DataFrame:
    employees['bonus']=((employees['employee_id']%2==1) & (~employees['name'].str.startswith('M')))*employees['salary']
    return employees[['employee_id', 'bonus']].sort_values(by='employee_id')

## 2 Problem 2 : Fix Names in a Table	(	https://leetcode.com/problems/fix-names-in-a-table/ )
<br>
Select user_id, Concat(upper(substring(name,1,1)), 
    lower(substring(name,2,length(name)-1))) as name
FROM users 
ORDER BY user_id

<br>

import pandas as pd

def fix_names(users: pd.DataFrame) -> pd.DataFrame:
    users['name']=users['name'].str.capitalize()
    result_df=users.sort_values(by='user_id', ascending=True)
    return result_df
    

## 3 Problem 3 : Patients with a Condition ( https://leetcode.com/problems/patients-with-a-condition/)
<br>
import pandas as pd

def find_patients(patients: pd.DataFrame) -> pd.DataFrame:
    with_diabetes=patients[patients['conditions'].str.contains(r'\bDIAB1')]
    result_df=with_diabetes[['patient_id','patient_name', 'conditions']]
    return result_df



