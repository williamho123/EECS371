# EECS 371 - Academic Advisor

Any KRF files that need to be loaded should be loaded through the Companions interface.

A high level overview of each file:
- Courses.krf : contains the courses for different majors with the structure (course ?courseNum ?courseLevel ?major) (Deprecated)
- Distros.krf : contains the logic to see if a student has passed distro requirements as well as all available distro courses.
- Econ.krf : contains the logic representing requirements needed for an Econ major, as well as courses that statisfy its requirments.
- GeneralReqs.krf : contains high level query predicates that the are available to the user.

## Load GeneralReqs.krf, William.krf, Julie.krf, Econ.krf, Distro.krf

The first feature of our model is the ability for an advisor to see if any of their students have completed their degree.

## Use the query: (earnedDegree ?student ?major)

This query will return all students that have completed a Weinberg degree (including distros) in any major.
Note that you can also bind the ?student and ?major variables for a more precise query (e.g. (earnedDegree William Economics))

By running this query, you notice that while William has in fact completed an economics degree, Julie has not.

## Use the query: (requirementNotMet ?student ?major ?r)

This query will return the set of all requirments that a student has yet to complete to earn degree with some major.
Note that while ?student and ?major can be bound, ?r should be left free as it is the return variable.
(e.g. (requirementNotMet Julie Electives ?r))

## Use the query: (passedRequirementCourse ?student ?requirement ?course) 

This query will return all course passed by some student that fulfill some requirement.
All or some of these variables can be bound for more precision (e.g. (passedRequirementCourse Julie Econ_FieldCourseRequirment ?course))
Predicates that work with this query include: Econ_FieldCourseRequirement, Econ_RelatedFieldsCourseRequirement, Econ_EconometricsRequirement, Econ_StatsRequirement.

## Use the query: (completedDistroArea ?student ?area) 

This query will return all distro areas (numbered I through VI) that have been completed by some student.
Both of these variables may be bound (e.g. (completedDistroArea William IV))
