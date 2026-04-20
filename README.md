# BME3053C-project
import math
class cardiovascular_risk:
  def __init__(self, sex, age, total_cholesterol, HDL_cholesterol, systolic_blood_pressure, smoker, diabetes, blood_pressure_medication):
    self.sex = sex
    self.age = age
    self.total_cholesterol = total_cholesterol
    self.HDL_cholesterol = HDL_cholesterol
    self.systolic_blood_pressure = systolic_blood_pressure
    self.smoker = 0
    self.diabetes = 0
    self.blood_pressure_medication = 0

  def calculate_risk_c(self):
    if self.sex == "male":
      if self.blood_pressure_medication == 0:
        exponent = (12.344*math.log(self.age)) + (11.853*math.log(self.total_cholesterol)) - (2.664*math.log(self.age*self.total_cholesterol)) - (7.99*math.log(self.HDL_cholesterol)) + (1.769*math.log(self.age*self.HDL_cholesterol)) + (1.764*math.log(self.systolic_blood_pressure)) + (7.837*self.smoker) - (1.795*math.log(self.age)*self.smoker) + (.658*self.diabetes)
      elif self.blood_pressure_medication == 1:
        exponent = (12.344*math.log(self.age)) + (11.853*math.log(self.total_cholesterol)) - (2.664*math.log(self.age*self.total_cholesterol)) - (7.99*math.log(self.HDL_cholesterol)) + (1.769*math.log(self.age*self.HDL_cholesterol)) + (1.797*math.log(self.systolic_blood_pressure)) + (7.837*self.smoker) - (1.795*math.log(self.age)*self.smoker) + (.658*self.diabetes)
      risk_c = 1 - (.9144**(exponent - 61.18))
      percent_risk_c = risk_c*100
    elif self.sex == "female":
      if self.blood_pressure_medication == 0:
        exponent = (-29.799*math.log(self.age)) + (4.884*(math.log(self.age))**2) + (13.52*math.log(self.total_cholesterol)) - (3.114*math.log(self.age*self.total_cholesterol)) - (13.578*math.log(self.HDL_cholesterol)) + (3.149*math.log(self.age*self.HDL_cholesterol)) + (1.957*math.log(self.systolic_blood_pressure)) + (7.574*self.smoker) - (1.665*math.log(self.age)*self.smoker) + (.661*self.diabetes)
      elif self.blood_pressure_medication == 1:
        exponent = (-29.799*math.log(self.age)) + (4.884*(math.log(self.age))**2) + (13.52*math.log(self.total_cholesterol)) - (3.114*math.log(self.age*self.total_cholesterol)) - (13.578*math.log(self.HDL_cholesterol)) + (3.149*math.log(self.age*self.HDL_cholesterol)) + (2.019*math.log(self.systolic_blood_pressure)) + (7.574*self.smoker) - (1.665*math.log(self.age)*self.smoker) + (.661*self.diabetes)
      risk_c = 1 - (.9665**(exponent - 86.61))
      percent_risk_c = risk_c*100
    if cardiovascular_family_history == 1:
      percent_risk_c = percent_risk_c + 1
    if percent_risk_c < 5:
      risk_group = "low"
    elif percent_risk_c > 20:
      risk_group = "high"
    else:
      risk_group = "moderate"
    print(f"Your 10-year cardiovascular risk is {percent_risk_c:.2f}% which means you are in the {risk_group} risk group.")

class hypertension_risk:
  def __init__(self, age, systolic_blood_pressure, diastolic_blood_pressure, body_mass_index, smoker, hypertension_parental_history):
    self.age = age
    self.systolic_blood_pressure = systolic_blood_pressure
    self.diastolic_blood_pressure = diastolic_blood_pressure
    self.body_mass_index = body_mass_index
    self.smoker = 0
    self.hypertension_parental_history = 0

  def calculate_risk_h(self):
    exponent = -7.88 + (.063*self.age) + (.013*self.systolic_blood_pressure) + (.033*self.diastolic_blood_pressure) + (.059*self.body_mass_index) + (.353*self.smoker) + (.293*self.hypertension_parental_history)
    risk_h = 1/(1+math.e**(-exponent))
    percent_risk_h = abs(risk_h*100)
    if percent_risk_h < 5:
      risk_group = "low"
    elif percent_risk_h > 20:
      risk_group = "high"
    else:
      risk_group = "moderate"
    print(f"Your 4-year hypertension risk is {percent_risk_h:.2f}% which means you are in the {risk_group} risk group.")

class main_factors:
  def __init__(self, age, total_cholesterol, HDL_cholesterol, systolic_blood_pressure, diastolic_blood_pressure, body_mass_index, smoker, diabetes, hypertension_parental_history, cardiovascular_family_history):
    self.age = age
    self.total_cholesterol = total_cholesterol
    self.HDL_cholesterol = HDL_cholesterol
    self.systolic_blood_pressure = systolic_blood_pressure
    self.diastolic_blood_pressure = diastolic_blood_pressure
    self.body_mass_index = body_mass_index
    self.smoker = smoker
    self.diabetes = diabetes
    self.hypertension_parental_history = hypertension_parental_history
    self.cardiovascular_family_history = cardiovascular_family_history
  
  def factors(self):
    if age > 60:
      print("Your age is playing a factor in your higher risk for cardiovascular events and hypertension.")
    if total_cholesterol > 200:
      print("Your total cholesterol is over the normal (200mg/dL) which is playing a factor in your higher risk for cardiovascular events.")
    if HDL_cholesterol < 60:
      print("Your HDL cholesterol is under the normal (60mg/dL) which is playing a factor in your higher risk for cardiovascular events.")
    if systolic_blood_pressure > 120:
      print("Your systolic blood pressure is over the normal (120mmHg) which is playing a factor in your higher risk for cardiovascular events and hypertension.")
    if diastolic_blood_pressure > 80:
      print("Your diastolic blood pressure is over the normal (80mmHg) which is playing a factor in your higher risk for hypertension.")
    if body_mass_index > 25:
      print("Your body mass index is over the normal (25kg/m^2) which is playing a factor in your higher risk for hypertension.")
    if body_mass_index < 18.5:
      print("Your body mass index is under the normal (18.5kg/m^2) which is unhealthy.")
    if smoker == 1:
      print("You being a smoker is playing a factor in your higher risk for cardiovascular events and hypertension.")
    if diabetes == 1:
      print("You being a diabetic is playing a factor in your higher risk for cardiovascular events.")
    if hypertension_parental_history == 1:
      print("You having parental history of hypertension is playing a factor in your higher risk for hypertension.")
    if cardiovascular_family_history == 1:
      print("You having family history of cardiovascular events is playing a factor in your higher risk for cardiovascular events.")

sex = input("What is your sex? (male or female): ")
age = float(input("What is your age? (in years): "))
total_cholesterol = float(input("What is your total cholesterol? (in mg/dL): "))
HDL_cholesterol = float(input("What is your HDL cholesterol? (in mg/dL): "))
systolic_blood_pressure = float(input("What is your systolic blood pressure (in mmHg): "))
diastolic_blood_pressure = float(input("What is your diastolic blood pressure (in mmHg): "))
body_mass_index = float(input("What is your body mass index? (in kg/m^2): "))
smoker = float(input("Do you smoke? (0 if no, 1 if yes): "))
diabetes = float(input("Do you have diabetes? (0 if no, 1 if yes): "))
blood_pressure_medication = float(input("Are you on blood pressure medication? (0 if no, 1 if yes): "))
hypertension_parental_history = float(input("Do you have a parental history of hypertension? (0 if no, 1 if yes): "))
cardiovascular_family_history = float(input("Do you have a family history of cardiovascular events? (0 if no, 1 if yes): "))

participant_c = cardiovascular_risk(sex, age, total_cholesterol, HDL_cholesterol, systolic_blood_pressure, smoker, diabetes, blood_pressure_medication)
participant_c.calculate_risk_c()
participant_h = hypertension_risk(age, systolic_blood_pressure, diastolic_blood_pressure, body_mass_index, smoker, hypertension_parental_history)
participant_h.calculate_risk_h()
participant_f = main_factors(age, total_cholesterol, HDL_cholesterol, systolic_blood_pressure, diastolic_blood_pressure, body_mass_index, smoker, diabetes, hypertension_parental_history, cardiovascular_family_history)
participant_f.factors()
