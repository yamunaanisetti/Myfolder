# ndd
nested drop downs
<html>
<head>
<title>
nested drop downs
</title>
<script>
var country=new Array("Afghanisthan","India");
var state=new Array();
state[0]="";
state[1]="A|B|C";
state[2]="AndhraPrdesh|telangana";
var city=new Array();
city[0]="";
city[1,1]="X|Y|Z";
city[1,2]="A|B|C";
city[1,3]="d|e|f";
city[2,1]="vizag|kakinada|eluru|rjy";
city[2,2]="hyd|sec";


  function populatecountries(cId,sId,tId)
{
 
 	var countryElement=document.getElementById(cId);
	countryElement.length=0;
	countryElement.options[0]=new Option("select country",'-1');
	countryElement.selectedIndex=0;

		for(var i=0;i<country.length;i++)
		{

			countryElement.options[countryElement.length]=new Option(country[i],country[i]) ;
		}
		if(sId)
			{
			countryElement.onchange=function ()
				{
				populatestates(cId,sId,tId);
				};
			}
}

function populatestates(cId,sId,tId)
{
	 var countrySelectedIndex=document.getElementById(cId).selectedIndex;
	 var stateElement=document.getElementById(sId);
 	stateElement.length=0;
	stateElement.options[0]=new Option('selectstate','');
	stateElement.selectedIndex=0;

	var state_arr=state[countrySelectedIndex].split('|');

		for(var i=0;i<=state_arr.length;i++)
		{
			stateElement.options[stateElement.length]=new Option(state_arr[i],state_arr[i]);

		}
		if(tId)
		{
			stateElement.onchange=function()
			{

			populateCities(cId,sId,tId);

			};

		}
}
function populateCities(cId,sId,tId)
{       
  	var stateselectedIndex=document.getElementById(sId).selectedIndex;
  	var cityElement=document.getElementById(tId);
  	cityElement.length=0;
  	cityElement.options[0]=new Option('select city','');
  	cityElement.selectedIndex=0;
  	var city_arr=city[stateselectedIndex].split('|');
	
	for(var i=0;i<city_arr.length;i++)
		{
		cityElement.options[cityElement.length]=new Option(city_arr[i],city_arr[i]);
		}


}

</script>
</head>
<body>
SELECT COUNTRY:
<select id="country" name="country">
</select><br>
SELECT STATE:
<select id="state" name="state">
</select><br>
SELECT CITY:
<select id="city" name="city"
</select><br>
<script language="javascript">
populatecountries("country","state","city");

</script>
</body>

</html>
