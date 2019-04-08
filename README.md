# Express-mail-project
Verify calculator operation as "Рассчитать стоимость доставки" depending on what dataset were entry criteria for some tests.. 

To start testing of "calculator-Express Mail" go to http://express-mail.net/calc/ 

specs overview:
- http://express-mail.net/prices/local/  - only "Вес" and "Стандарт" columns will be considered (see set data below)
- http://express-mail.net/modules/files/docs/rules_tov.pdf  - here maximum weight pointed as 20kg

Requirements to "Вес" field:
- *required field
- till 20 kg accepted valid to be according to spec 
- only digits (using logic)

Pre-conditions/Entry сriteria for these fields:

- "Внутригородская доставка" (by default) 
- "Категория": Стандарт (by default)
- "Вес"： <no data> (to calculate delivery cost user must type any digits like data till 20 kg)


  ---Вес---   ---Стандарт---     (see spec: http://express-mail.net/prices/local/)
1. до 0,2      -- 42 
2. 0,2 - 1,0   -- 48
3. (+) 1 кг.   -- 5

Inputs data for "Вес" using design techniques(to create test cases):
/allowable range 0,1 - 20 kg/
- type 0,1      --- expected result = 42
- type 0,19     --- expected result = 42
- type 0,2      --- expected result = 42
- type 0,21     --- expected result = 48
- type 0,999999 --- expected result = 48
- type 1，0 or 1 --- expected result = 48
- type 1,9      --- expected result = 53
- type 2        --- expected result = 48(1kg) + 5(+1kg)= 48 + 5*1 = 53
- type 8        --- expected result = 48(1kg) + 5(+7kg)= 48 + 5*7 = 83
- type 20       --- expected result = 48(1kg) + 5(+19kg)= 48 + 5*19 = 143
- type 20,9     --- expected result = 48(1kg) + 5(+20kg)= 48 + 5*20 = 148 - no message (accepted till 20kg)
- type 21     --- expected result = 48(1kg) + 5(+20kg)= 48 + 5*20 = 148 - no message (accepted till 20kg) - probably bug or need identify 
